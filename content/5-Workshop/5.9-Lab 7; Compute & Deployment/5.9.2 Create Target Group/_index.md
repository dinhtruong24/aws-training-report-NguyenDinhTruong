---
title : "Create Target Group"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.9.2. </b> "
---

In this section, we will create a **Target Group** to manage the Amazon EC2 instances that receive traffic from the **Application Load Balancer (ALB)**.

A Target Group acts as the connection between the Load Balancer and the EC2 instances. It maintains a list of registered targets and performs **Health Checks** to ensure that only healthy instances receive incoming requests.

---

## Step 1. Open Target Groups

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon EC2** service.
2. In the navigation pane, select **Target Groups**.
3. Click **Create target group**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.2-create-target-group.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.3. Creating a Target Group.</i>
</p>

---

## Step 2. Configure the Target Group

On the **Create target group** page, perform the following steps:

1. Select **Instances** as the target type.
2. Enter the Target Group name.
3. Configure the **Protocol** and **Port**.
4. Select the appropriate **VPC**.
5. Configure the **Health Check** settings.
6. Click **Next** to continue.

Example:

```text
delivery-target-group
```

---

## Step 3. Register EC2 Instances

After configuring the Target Group:

1. Select the EC2 instances to register.
2. Click **Include as pending below**.
3. Click **Create target group**.

After the Target Group has been created successfully:

- Open the **Target Groups** list.
- Verify that the Target Group has been created.
- Check the Health Check status of the registered EC2 instances.
- Confirm that the Target Group is ready to be associated with the Application Load Balancer.

---

## Configuration Summary

| Property | Value |
|---|---|
| AWS Service | Amazon EC2 |
| Resource | Target Group |
| Target Type | Instances |
| Protocol | HTTP |
| Port | 80 |
| Health Check | Enabled |
| Status | Healthy |

---

## Result

After completing this section, you have successfully:

- Created a Target Group.
- Configured Health Check settings.
- Registered EC2 instances.
- Prepared the Target Group for integration with the Application Load Balancer.

In the next section, we will continue with **5.9.3 – Create Application Load Balancer**.