---
title : "Create Security Groups"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.4.1. </b> "
---

In this section, we will create **Security Groups** to control network traffic between the different components of the system.

Three Security Groups will be created:

- A Security Group for the Application Load Balancer.
- A Security Group for the EC2 Application Server.
- A Security Group for Amazon RDS.

Separating Security Groups for each component improves security by allowing only the required communication between system resources.

---

## Step 1. Create a Security Group for the Application Load Balancer

Sign in to the **AWS Management Console**, open the **EC2** service, and perform the following steps:

1. Select **Security Groups**.
2. Click **Create security group**.
3. Enter the following Security Group name:

```text
delivery-alb-sg
```

4. Description:

```text
Security Group for Application Load Balancer
```

5. Select the VPC:

```text
delivery-dev-vpc
```

6. Configure the following Inbound Rules:

| Type | Port | Source |
|------|------|--------|
| HTTP | 80 | 0.0.0.0/0 |
| HTTPS | 443 | 0.0.0.0/0 |

7. Click **Create security group**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-alb-security-group.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.1. Creating the Security Group for the Application Load Balancer.</i>
</p>

---

## Step 2. Create a Security Group for the EC2 Instance

Create another Security Group.

Enter the following name:

```text
delivery-ec2-sg
```

Description:

```text
Security Group for EC2
```

Select the same VPC:

```text
delivery-dev-vpc
```

Configure the following Inbound Rules:

| Type | Port | Source |
|------|------|--------|
| HTTP | 80 | delivery-alb-sg |
| HTTPS | 443 | delivery-alb-sg |

This configuration ensures that only the Application Load Balancer can communicate with the EC2 application server.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-ec2-security-group.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.2. Creating the Security Group for the EC2 application server.</i>
</p>

---

## Step 3. Create a Security Group for Amazon RDS

Create the final Security Group.

Enter the following name:

```text
delivery-rds-sg
```

Description:

```text
Security Group for Amazon RDS
```

Configure the following Inbound Rule:

| Type | Port | Source |
|------|------|--------|
| MySQL/Aurora | 3306 | delivery-ec2-sg |

This rule ensures that only the EC2 application server is allowed to connect to the Amazon RDS database.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-rds-security-group.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.3. Creating the Security Group for Amazon RDS.</i>
</p>

---

## Result

After completing this section, you have successfully:

- Created the Security Group for the Application Load Balancer.
- Created the Security Group for the EC2 application server.
- Created the Security Group for Amazon RDS.
- Configured network access rules between the system components.
- Completed the Security Group configuration for Lab 2.

In the next section, we will continue with **5.4.2 – Configure IAM Role and IAM Policy**.