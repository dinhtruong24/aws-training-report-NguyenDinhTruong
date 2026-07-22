---
title : "Create Auto Scaling Group"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.9.4. </b> "
---

In this section, we will create an **Auto Scaling Group (ASG)** to automatically manage the number of Amazon EC2 instances based on the application's workload.

An Auto Scaling Group maintains the desired number of EC2 instances and automatically scales the infrastructure according to traffic demand. When combined with a Launch Template and an Application Load Balancer, it provides a highly available and scalable deployment environment.

---

## Step 1. Open Auto Scaling Groups

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon EC2** service.
2. In the navigation pane, select **Auto Scaling Groups**.
3. Click **Create Auto Scaling group**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.4-create-auto-scaling-group.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.5. Creating an Auto Scaling Group.</i>
</p>

---

## Step 2. Configure the Auto Scaling Group

On the **Create Auto Scaling group** page, perform the following steps:

1. Enter the Auto Scaling Group name.
2. Select the Launch Template created in the previous section.
3. Select the appropriate **VPC** and **Subnets**.
4. Attach the **Application Load Balancer**.
5. Select the Target Group.
6. Configure the **Desired Capacity**, **Minimum Capacity**, and **Maximum Capacity**.
7. Click **Create Auto Scaling group**.

Example:

```text
delivery-auto-scaling-group
```

---

## Step 3. Verify the Auto Scaling Group

After the Auto Scaling Group has been created successfully:

- Open the **Auto Scaling Groups** list.
- Verify the status of the Auto Scaling Group.
- Confirm that EC2 instances have been launched using the Launch Template.
- Verify that the instances have been registered with the Target Group.
- Ensure that the Auto Scaling Group status is **In Service**.

---

## Configuration Summary

| Property | Value |
|---|---|
| AWS Service | Amazon EC2 Auto Scaling |
| Resource | Auto Scaling Group |
| Launch Template | `delivery-launch-template` |
| Target Group | `delivery-target-group` |
| Desired Capacity | 2 |
| Minimum Capacity | 2 |
| Maximum Capacity | 4 |
| Status | In Service |

---

## Result

After completing this section, you have successfully:

- Created an Auto Scaling Group.
- Associated the Launch Template with the Auto Scaling Group.
- Connected the Auto Scaling Group to the Application Load Balancer.
- Verified that the EC2 instances are running correctly.
- Completed a scalable deployment environment with automatic scaling.

After completing Lab 7, the system is ready to serve application traffic with load balancing and automatic scaling capabilities.