---
title : "Create Launch Template"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.9.1. </b> "
---

In this section, we will create a **Launch Template** to define the standard configuration for Amazon EC2 instances that will be deployed in the Auto Scaling Group.

A Launch Template stores the configuration required to launch EC2 instances, including the Amazon Machine Image (AMI), Instance Type, Key Pair, Security Group, and network settings. Using a Launch Template ensures that EC2 instances are deployed consistently and simplifies the process of scaling the application infrastructure.

---

## Step 1. Open the Amazon EC2 Service

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Search for **Amazon EC2**.
2. Open the **EC2 Dashboard**.
3. In the navigation pane, select **Launch Templates**.
4. Click **Create launch template**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-create-launch-template.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.2. Creating a Launch Template.</i>
</p>

---

## Step 2. Configure the Launch Template

On the **Create launch template** page, perform the following steps:

1. Enter the **Launch Template Name**.
2. Select the **Amazon Machine Image (AMI)**.
3. Choose the **Instance Type**.
4. Select the **Key Pair**.
5. Configure the **Security Group**.
6. Review the remaining settings.
7. Click **Create launch template**.

Example:

```text
delivery-launch-template
```

---

## Step 3. Verify the Launch Template

After the Launch Template has been created successfully:

- Open the **Launch Templates** list.
- Verify that the new Launch Template appears.
- Review the template configuration.
- Confirm that it is ready to be used by the Auto Scaling Group.

---

## Configuration Summary

| Property | Value |
|---|---|
| AWS Service | Amazon EC2 |
| Resource | Launch Template |
| Template Name | `delivery-launch-template` |
| Instance Type | t2.micro (example) |
| Status | Available |

---

## Result

After completing this section, you have successfully:

- Accessed the Amazon EC2 service.
- Created a Launch Template.
- Configured the deployment settings for EC2 instances.
- Prepared the Launch Template for use with an Auto Scaling Group.

In the next section, we will continue with **5.9.2 – Create Target Group**.