---
title : "Lab 2: Security Groups and IAM"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.4. </b> "
---

In this lab, we will build the security layer of the system by configuring **Security Groups**, an **IAM Role**, and an **IAM Policy**.

Security Groups are used to control network traffic between the Application Load Balancer, EC2 application server, and Amazon RDS. Each component will use a separate Security Group, helping restrict connections and allowing only the required communication paths.

In addition, an IAM Role for EC2 will be created so that the application can access AWS services using temporary credentials. This approach avoids storing Access Keys and Secret Access Keys directly in the application source code or configuration files.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-alb-security-group.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.1. Configuring the security layer for the system components.</i>
</p>

---

## Lab Objectives

After completing this lab, you will be able to:

- Create a Security Group for the Application Load Balancer.
- Create a Security Group for the EC2 application server.
- Create a Security Group for Amazon RDS.
- Restrict traffic between the ALB, EC2, and RDS components.
- Create an IAM Role for EC2 instances.
- Configure the Trust Relationship for EC2.
- Create a Runtime IAM Policy for the application.
- Attach the IAM Policy to the IAM Role.
- Verify the IAM identity using AWS STS.
- Verify access permissions for Amazon S3 and Amazon SQS.
- Apply the **Principle of Least Privilege**.
- Avoid using permanent Access Keys on EC2 instances.

---

## Security Architecture

The Security Groups in this lab are configured according to the following access chain:

```text
Internet
   ↓
Application Load Balancer
   ↓
EC2 Application Server
   ↓
Amazon RDS
```

Network access is controlled as follows:

| Component | Allowed Traffic |
|---|---|
| `delivery-alb-sg` | Allows HTTP and HTTPS traffic from the Internet |
| `delivery-ec2-sg` | Allows application traffic only from `delivery-alb-sg` |
| `delivery-rds-sg` | Allows MySQL connections only from `delivery-ec2-sg` |

This configuration prevents Amazon RDS from being accessed directly from the Internet. The EC2 application server also receives traffic only through the Application Load Balancer.

---

## IAM Configuration

The EC2 instances will use the following IAM Role:

```text
delivery-ec2-role
```

The IAM Role will have the following Runtime Policy attached:

```text
delivery-runtime-policy
```

The Runtime Policy provides the permissions required for the application to interact with AWS services such as:

- Amazon S3
- Amazon SQS
- AWS STS
- Other supporting services used by the system

Permissions should be restricted to only the required actions and resources according to the following principle:

```text
Principle of Least Privilege
```

---

## Lab Contents

Lab 2 is divided into three sections:

### 5.4.1 Create Security Groups

In this section, we will:

- Create `delivery-alb-sg`.
- Allow HTTP and HTTPS traffic from the Internet to the Application Load Balancer.
- Create `delivery-ec2-sg`.
- Allow only the Application Load Balancer to access the EC2 instances.
- Create `delivery-rds-sg`.
- Allow only EC2 instances to connect to Amazon RDS through MySQL port 3306.

### 5.4.2 Configure IAM Role and IAM Policy

In this section, we will:

- Create the `delivery-ec2-role` IAM Role.
- Select EC2 as the trusted entity.
- Verify the Trust Relationship.
- Create the `delivery-runtime-policy` Runtime Policy.
- Configure access permissions for the required AWS services.
- Attach the Runtime Policy to the IAM Role.

### 5.4.3 Verify IAM Permissions

In this section, we will:

- Attach the IAM Role to an EC2 instance.
- Verify the AWS identity using AWS STS.
- Verify access to Amazon S3.
- Verify access to Amazon SQS.
- Confirm that the application uses temporary credentials.
- Verify the Principle of Least Privilege.
- Troubleshoot `Unable to locate credentials` and `AccessDenied` errors.

---

## Expected Results

After completing Lab 2:

- Three Security Groups have been created and configured correctly.
- Network traffic between the ALB, EC2 instances, and Amazon RDS is controlled.
- Amazon RDS cannot be accessed directly from the Internet.
- The IAM Role for EC2 has been created.
- The Runtime IAM Policy has been attached to the IAM Role.
- EC2 instances can obtain temporary AWS credentials.
- The application can access the AWS services for which permissions have been granted.
- Access Keys and Secret Access Keys do not need to be stored on the EC2 instances.
- The system has an appropriate network security and AWS access-control layer.

After completing Lab 2, the system will be ready for **Lab 3 – Amazon S3 Storage**.