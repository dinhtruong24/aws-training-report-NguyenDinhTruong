---
title : "Create Target Group"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.9.2. </b> "
---

In this section, we will create a **Target Group** named `delivery-app-tg` to receive traffic from the Application Load Balancer and forward requests to the Amazon EC2 instances running the application.

According to the workshop configuration, the application listens on **HTTP port 5000**. The Target Group performs health checks to ensure that only healthy EC2 instances receive incoming traffic.

---

## Step 1. Open Target Groups

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon EC2** service.
2. In the navigation pane, select **Target Groups**.
3. Click **Create target group**.
4. Choose the appropriate target type for the EC2 instances.

---

## Step 2. Configure the Target Group

Configure the Target Group with the following settings:

| Property | Value |
|---|---|
| Target Group Name | `delivery-app-tg` |
| Protocol | HTTP |
| Port | `5000` |
| Target Type | EC2 Instances |
| Health Check Protocol | HTTP |
| Health Check Path | `/` or a dedicated health endpoint |

The Target Group uses **HTTP port 5000**, which matches the listening port of the application running on the EC2 instances.

The health check can use the root path (`/`) or a dedicated health endpoint provided by the application. The selected endpoint must return a successful HTTP response so that the instance is marked as **Healthy**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-verify-email-identity.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.2. Target Group <b>delivery-app-tg</b> on HTTP port 5000.</i>
</p>

---

## Step 3. Register EC2 Instances

After configuring the Target Group:

1. Select the EC2 instances running the application.
2. Register the instances with `delivery-app-tg`.
3. Confirm that the traffic port is `5000`.
4. Complete the Target Group creation process.

The EC2 instances are launched from the `delivery-ec2-lt` Launch Template and run in the private application subnets.

---

## Step 4. Verify Health Checks

After the Target Group has been created:

- Open the `delivery-app-tg` Target Group.
- Select the **Targets** tab.
- Verify that the EC2 instances are registered.
- Confirm that the health check uses port `5000`.
- Check the health status of each instance.

Expected status:

```text
Healthy
```

If an instance is not healthy, verify the following:

- The `delivery.service` service is running.
- The application is listening on port `5000`.
- The `delivery-ec2-sg` security group allows traffic from `delivery-alb-sg`.
- The configured health check path returns a successful HTTP response.

---

## Traffic Flow

The Target Group sits between the Application Load Balancer and the EC2 instances.

```text
Application Load Balancer
            │
            ▼
delivery-app-tg
HTTP:5000
            │
            ▼
Amazon EC2 Instances
            │
            ▼
delivery.service
```

The Application Load Balancer forwards requests only to EC2 instances that are reported as **Healthy** by the Target Group.

---

## Result

After completing this section, you have successfully:

- Created the `delivery-app-tg` Target Group.
- Configured HTTP traffic on port `5000`.
- Configured application health checks.
- Registered the EC2 instances with the Target Group.
- Prepared the Target Group for integration with the Application Load Balancer.