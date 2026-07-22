---
title : "Create Application Load Balancer"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.9.3. </b> "
---

In this section, we will create an **Application Load Balancer (ALB)** to distribute incoming traffic to Amazon EC2 instances through a Target Group.

An Application Load Balancer is a Layer 7 load balancing service that routes HTTP and HTTPS requests to the appropriate backend resources. When combined with a Target Group and an Auto Scaling Group, the ALB improves the application's availability, reliability, and scalability.

---

## Step 1. Open Application Load Balancers

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon EC2** service.
2. In the navigation pane, select **Load Balancers**.
3. Click **Create Load Balancer**.
4. Choose **Application Load Balancer**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.3-create-application-load-balancer.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.4. Creating an Application Load Balancer.</i>
</p>

---

## Step 2. Configure the Application Load Balancer

On the configuration page, perform the following steps:

1. Enter the Load Balancer name.
2. Select **Internet-facing**.
3. Choose **IPv4** as the IP address type.
4. Select the required **Availability Zones**.
5. Configure the **Security Group**.
6. Select the Target Group created in the previous section.
7. Click **Create Load Balancer**.

Example:

```text
delivery-alb
```

---

## Step 3. Verify the Application Load Balancer

After the Application Load Balancer has been created successfully:

- Open the **Load Balancers** list.
- Verify the status of the Application Load Balancer.
- Confirm that the listener has been configured correctly.
- Verify that the Target Group has been associated successfully.
- Ensure that the Load Balancer status is **Active**.

---

## Configuration Summary

| Property | Value |
|---|---|
| AWS Service | Elastic Load Balancing |
| Resource | Application Load Balancer |
| Scheme | Internet-facing |
| IP Address Type | IPv4 |
| Listener | HTTP : 80 |
| Target Group | `delivery-target-group` |
| Status | Active |

---

## Result

After completing this section, you have successfully:

- Created an Application Load Balancer.
- Configured the listener.
- Associated the Target Group with the Load Balancer.
- Prepared the load balancing infrastructure for the application.

In the next section, we will continue with **5.9.4 – Create Auto Scaling Group**.