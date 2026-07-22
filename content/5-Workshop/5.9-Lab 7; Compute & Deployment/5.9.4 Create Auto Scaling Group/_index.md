---
title : "Create Auto Scaling Group"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.9.4. </b> "
---

In this section, we will create an **Auto Scaling Group (ASG)** using the `delivery-ec2-lt` Launch Template to manage the Amazon EC2 instances running the application.

The Auto Scaling Group is deployed across the two private application subnets, `app-a` and `app-b`. It maintains the desired number of EC2 instances and replaces an instance when it is no longer operating correctly.

After configuring the Auto Scaling Group, we will verify the application status, confirm the HTTP health check, and perform a rollback if the new release fails.

---

## Step 1. Open Auto Scaling Groups

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon EC2** service.
2. In the navigation pane, select **Auto Scaling Groups**.
3. Click **Create Auto Scaling group**.
4. Enter a name for the Auto Scaling Group.
5. Select the `delivery-ec2-lt` Launch Template.

---

## Step 2. Configure the Auto Scaling Group

Configure the Auto Scaling Group with the following settings:

| Property | Value |
|---|---|
| Launch Template | `delivery-ec2-lt` |
| VPC | `delivery-dev-vpc` |
| Subnets | `app-a` and `app-b` |
| Target Group | `delivery-app-tg` |
| Minimum Capacity | `1` |
| Desired Capacity | `1` |
| Maximum Capacity | Based on the workshop budget |
| Health Check | Elastic Load Balancing |
| Application Service | `delivery.service` |
| Executable | `/opt/delivery/current/WedNightFury` |

The EC2 instances are deployed in private application subnets and do not require public IP addresses.

Instance administration is performed through **AWS Systems Manager Session Manager** instead of exposing SSH access directly to the Internet.

---

## Step 3. Attach the Target Group

During the Auto Scaling Group creation process:

1. Select the option to attach an existing Load Balancer.
2. Select the following Target Group:

```text
delivery-app-tg
```

3. Enable Elastic Load Balancing health checks.
4. Confirm that the Target Group uses HTTP port `5000`.
5. Complete the Auto Scaling Group creation process.

Traffic flow:

```text
Internet
    │
    ▼
delivery-alb
HTTP:80
    │
    ▼
delivery-app-tg
HTTP:5000
    │
    ▼
Auto Scaling Group
    │
    ▼
Amazon EC2 Instances
app-a / app-b
```

---

## Step 4. Verify the Auto Scaling Group

After the Auto Scaling Group has been created:

- Open the **Auto Scaling Groups** list.
- Select the newly created Auto Scaling Group.
- Verify that the Launch Template is `delivery-ec2-lt`.
- Confirm that the selected subnets are `app-a` and `app-b`.
- Verify that the desired capacity is `1`.
- Confirm that an EC2 instance has been launched.
- Verify that the instance is registered with `delivery-app-tg`.
- Confirm that the Target Group reports the instance as **Healthy**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-send-test-email.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.4. Auto Scaling Group using <b>delivery-ec2-lt</b>.</i>
</p>

---

## Step 5. Verify the Current Release

Connect to the EC2 instance through **AWS Systems Manager Session Manager**.

Verify the symbolic link for the active release:

```bash
readlink -f /opt/delivery/current
```

The result should point to the current release directory, for example:

```text
/opt/delivery/releases/20260722-09
```

The application executable is launched from:

```text
/opt/delivery/current/WedNightFury
```

---

## Step 6. Verify the Service Status

Check the status of `delivery.service`:

```bash
sudo systemctl status delivery.service --no-pager -l
```

Expected status:

```text
active (running)
```

If the service is not running, verify:

- The executable path.
- The execute permission of the `WedNightFury` file.
- The application environment variables.
- The systemd service logs.
- Connectivity to RDS and the required AWS services.

---

## Step 7. Verify the HTTP Response

Test the application directly on the EC2 instance:

```bash
curl -sS -o /dev/null \
  -w 'HTTP %{http_code}\n' \
  http://127.0.0.1:5000/
```

Expected result:

```text
HTTP 200
```

An HTTP `200` response confirms that the application is listening on port `5000` and responding successfully.

If HTTP `200` is not returned, verify:

- Whether `delivery.service` is running.
- Whether the application is bound to port `5000`.
- Whether the configured health-check path exists.
- Whether the application encountered an error during startup.

---

## Step 8. Review the Application Logs

Use the following command to review logs from the last five minutes:

```bash
sudo journalctl \
  -u delivery.service \
  --since "5 minutes ago" \
  --no-pager
```

Review the logs for errors related to:

- Application startup.
- Database connectivity.
- AWS Secrets Manager.
- Amazon S3.
- Amazon SQS.
- Amazon Location.
- IAM permissions.
- Configuration files or environment variables.

---

## Step 9. Perform a Rollback

Before deploying the new release, the previous release path was stored in:

```bash
PREVIOUS_RELEASE=$(readlink -f /opt/delivery/current)
```

If the new release fails, point the symbolic link back to the previous release:

```bash
sudo ln -sfn \
  "$PREVIOUS_RELEASE" \
  /opt/delivery/current.next
```

Replace the active symbolic link:

```bash
sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current
```

Restart the application service:

```bash
sudo systemctl restart delivery.service
```

After the rollback, verify the release and application status again:

```bash
readlink -f /opt/delivery/current

sudo systemctl status \
  delivery.service \
  --no-pager -l

curl -sS -o /dev/null \
  -w 'HTTP %{http_code}\n' \
  http://127.0.0.1:5000/
```

---

## Complete Health Check and Rollback Workflow

```bash
readlink -f /opt/delivery/current

sudo systemctl status \
  delivery.service \
  --no-pager -l

curl -sS -o /dev/null \
  -w 'HTTP %{http_code}\n' \
  http://127.0.0.1:5000/

sudo journalctl \
  -u delivery.service \
  --since "5 minutes ago" \
  --no-pager

# Roll back if the new release fails
sudo ln -sfn \
  "$PREVIOUS_RELEASE" \
  /opt/delivery/current.next

sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current

sudo systemctl restart delivery.service
```

---

## HTTP Cookie Configuration

In the workshop environment, when accessing the application through an Application Load Balancer using HTTP, the following setting may be enabled temporarily:

```text
Security__AllowInsecureHttpForTesting=true
```

This setting must be used **only temporarily for testing purposes**.

After CloudFront HTTPS is operational, change the setting to:

```text
Security__AllowInsecureHttpForTesting=false
```

Then test the following functions again:

- Login.
- Session handling.
- Cookies.
- Post-login redirection.

---

## Result

After completing this section, you have successfully:

- Created an Auto Scaling Group using `delivery-ec2-lt`.
- Deployed EC2 instances across `app-a` and `app-b`.
- Attached the Auto Scaling Group to `delivery-app-tg`.
- Configured the minimum and desired capacities as `1`.
- Verified the symbolic link for the active release.
- Verified the status of `delivery.service`.
- Confirmed that the application returns HTTP `200` on port `5000`.
- Reviewed the application logs using `journalctl`.
- Rolled back to the previous release when the new release failed.
- Completed Lab 7 on EC2, Application Load Balancer, Auto Scaling, and application deployment.