---
title : "Create Launch Template"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.9.1. </b> "
---

In this section, we will create the **Launch Template** for the application. The Launch Template stores the configuration required to launch Amazon EC2 instances used by the Auto Scaling Group.

The Launch Template is configured with an appropriate Amazon Machine Image (AMI), the `delivery-ec2-role` IAM instance profile, the `delivery-ec2-sg` security group, and the root volume configuration. The EC2 instances are deployed in the **private application subnets** and managed through **AWS Systems Manager Session Manager (SSM)**.

---

## Step 1. Create the Launch Template

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon EC2** service.
2. Select **Launch Templates**.
3. Click **Create launch template**.
4. Enter the Launch Template name.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-open-amazon-ses.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.1. Application Launch Template.</i>
</p>

---

## Step 2. Configure the Launch Template

Configure the Launch Template with the following settings:

| Property | Value |
|---|---|
| Launch Template | `delivery-ec2-lt` |
| Amazon Machine Image | Appropriate AMI |
| IAM Instance Profile | `delivery-ec2-role` |
| Security Group | `delivery-ec2-sg` |
| Root Volume | Configured as required |

The EC2 instances are deployed in the **private application subnets** and managed through **AWS Systems Manager Session Manager (SSM)** instead of direct SSH access.

---

## Step 3. Verify the Launch Template

After the Launch Template has been created successfully:

- Verify the `delivery-ec2-lt` Launch Template.
- Confirm that the IAM instance profile is attached.
- Verify the Security Group configuration.
- Verify the root volume configuration.
- Ensure that the Launch Template is ready for use by the Auto Scaling Group.

---

## Result

After completing this section, you have successfully:

- Created the `delivery-ec2-lt` Launch Template.
- Configured the Amazon Machine Image (AMI).
- Attached the `delivery-ec2-role` IAM instance profile.
- Configured the `delivery-ec2-sg` security group.
- Prepared the Launch Template for deploying EC2 instances in the Auto Scaling Group.