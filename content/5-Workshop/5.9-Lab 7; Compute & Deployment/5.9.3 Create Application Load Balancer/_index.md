---
title : "Create Application Load Balancer"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.9.3. </b> "
---

In this section, we will configure an **Application Load Balancer (ALB)** named `delivery-alb` to receive incoming traffic from the Internet and forward requests to the `delivery-app-tg` Target Group.

After the Application Load Balancer has been configured, we will deploy a new application release from Amazon S3 using the **symbolic link (symlink)** deployment strategy. This approach enables fast release switching and simplifies rollback if a deployment issue occurs.

---

## Step 1. Create an Application Load Balancer

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon EC2** service.
2. In the navigation pane, choose **Load Balancers**.
3. Click **Create Load Balancer**.
4. Select **Application Load Balancer**.
5. Enter the Load Balancer name:

```text
delivery-alb
```

---

## Step 2. Configure the Application Load Balancer

Configure the Application Load Balancer with the following settings:

| Property | Value |
|---|---|
| Load Balancer Name | `delivery-alb` |
| Load Balancer Type | Application Load Balancer |
| Scheme | Internet-facing |
| Network | `delivery-dev-vpc` |
| Availability Zones | `public-a` and `public-b` |
| Security Group | `delivery-alb-sg` |
| Listener | HTTP Port `80` |
| Target Group | `delivery-app-tg` |

The Application Load Balancer is deployed in two public subnets so it can receive requests from the Internet.

The HTTP listener on port `80` forwards incoming requests to the `delivery-app-tg` Target Group, which then routes traffic to the application running on **HTTP port 5000**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-compose-test-email.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.3. Application Load Balancer <b>delivery-alb</b>.</i>
</p>

---

## Step 3. Verify the Application Load Balancer

After the Application Load Balancer has been created:

- Open the **Load Balancers** list.
- Select `delivery-alb`.
- Verify the Load Balancer status.
- Confirm that both public subnets are configured.
- Verify that the security group is `delivery-alb-sg`.
- Check the HTTP listener on port `80`.
- Confirm that the listener forwards traffic to `delivery-app-tg`.

Expected status:

```text
Active
```

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
Amazon EC2 Instances
```

---

## Step 4. Prepare the Release Information

According to the workshop document, the sample deployment uses the following values:

```bash
RELEASE=20260722-09
PACKAGE=WedNightFury-linux-x64-v9.tar.gz
```

Where:

- `RELEASE` is the deployment version identifier.
- `PACKAGE` is the application package stored in Amazon S3.

The deployment package is located at:

```text
s3://delivery-dev-pod-nm2026a/deployments/
```

---

## Step 5. Download the Deployment Package

Run the following command on the EC2 instance:

```bash
sudo aws s3 cp \
  s3://delivery-dev-pod-nm2026a/deployments/$PACKAGE \
  /opt/delivery/packages/$PACKAGE \
  --region ap-southeast-1
```

This command downloads the deployment package from Amazon S3 into:

```text
/opt/delivery/packages/
```

The EC2 instance uses the `delivery-ec2-role` IAM Instance Profile to access Amazon S3 without storing access keys on the server.

---

## Step 6. Extract the Release

Create a directory for the new release:

```bash
sudo mkdir -p /opt/delivery/releases/$RELEASE
```

Extract the deployment package:

```bash
sudo tar -xzf /opt/delivery/packages/$PACKAGE \
  -C /opt/delivery/releases/$RELEASE
```

Update the ownership:

```bash
sudo chown -R deliveryapp:deliveryapp \
  /opt/delivery/releases/$RELEASE
```

Grant execute permission:

```bash
sudo chmod +x \
  /opt/delivery/releases/$RELEASE/WedNightFury
```

The new release is stored in:

```text
/opt/delivery/releases/20260722-09
```

---

## Step 7. Save the Current Release

Before switching to the new release, save the current release path:

```bash
PREVIOUS_RELEASE=$(readlink -f /opt/delivery/current)
```

The `PREVIOUS_RELEASE` variable is used for rollback if the new deployment fails.

To verify its value:

```bash
echo "$PREVIOUS_RELEASE"
```

---

## Step 8. Switch the Symlink

Create a temporary symbolic link:

```bash
sudo ln -sfn \
  /opt/delivery/releases/$RELEASE \
  /opt/delivery/current.next
```

Replace the current symbolic link:

```bash
sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current
```

This approach minimizes downtime during deployment.

Resulting structure:

```text
/opt/delivery/releases/20260722-09
                 ▲
                 │
/opt/delivery/current
```

---

## Step 9. Restart the Service

Restart the application service:

```bash
sudo systemctl restart delivery.service
```

The application is managed by:

```text
delivery.service
```

Executable path:

```text
/opt/delivery/current/WedNightFury
```

---

## Complete Deployment Workflow

```bash
RELEASE=20260722-09
PACKAGE=WedNightFury-linux-x64-v9.tar.gz

sudo aws s3 cp \
  s3://delivery-dev-pod-nm2026a/deployments/$PACKAGE \
  /opt/delivery/packages/$PACKAGE \
  --region ap-southeast-1

sudo mkdir -p /opt/delivery/releases/$RELEASE

sudo tar -xzf /opt/delivery/packages/$PACKAGE \
  -C /opt/delivery/releases/$RELEASE

sudo chown -R deliveryapp:deliveryapp \
  /opt/delivery/releases/$RELEASE

sudo chmod +x \
  /opt/delivery/releases/$RELEASE/WedNightFury

PREVIOUS_RELEASE=$(readlink -f /opt/delivery/current)

sudo ln -sfn \
  /opt/delivery/releases/$RELEASE \
  /opt/delivery/current.next

sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current

sudo systemctl restart delivery.service
```

---

## Migration Notes

If the new release only changes:

- Amazon S3
- Amazon SQS
- Amazon Location
- JavaScript
- Application configuration without database schema changes

then **database migration should not be executed**.

```text
No schema changes → No migration required
```

Run database migration only when the release includes schema changes and an appropriate backup has been completed.

---

## Result

After completing this section, you have successfully:

- Created the `delivery-alb` Application Load Balancer.
- Deployed the Load Balancer across two public subnets.
- Attached the `delivery-alb-sg` security group.
- Connected the Load Balancer to the `delivery-app-tg` Target Group.
- Downloaded the application package from Amazon S3.
- Extracted the application into a dedicated release directory.
- Saved the current release before deployment.
- Updated the `/opt/delivery/current` symbolic link.
- Restarted the `delivery.service`.
- Prepared the environment for quick rollback if the new release fails.