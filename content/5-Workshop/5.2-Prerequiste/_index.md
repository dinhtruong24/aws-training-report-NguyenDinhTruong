---
title : "Prerequisites"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

To successfully deploy the **Delivery Management System on AWS**, you need to prepare an AWS account, the required access permissions, administration tools, and application configuration information.

Completing the following prerequisites will help ensure a smooth workshop experience and reduce errors when deploying networking, database, storage, event-processing, and Amazon EC2 application resources.

---

## 1. AWS Account

You need an active AWS account to create and manage the services used throughout this workshop.

The account must be fully activated and have a valid payment method. Some resources may incur charges during the workshop, especially:

- NAT Gateway.
- Amazon RDS for MySQL.
- Application Load Balancer.
- Amazon EC2.
- Amazon Location Service.
- Amazon Route 53 or Amazon CloudFront, if used.

Monitor your AWS costs regularly and complete the **Cleanup** section after finishing the workshop.

---

## 2. Select an AWS Region

All resources in this workshop are deployed in the same AWS Region to ensure that the services can communicate correctly.

The workshop uses:

```text
Asia Pacific (Singapore)
ap-southeast-1
```

Before creating any resources, verify the selected Region in the upper-right corner of the AWS Management Console.

Using the correct Region is especially important for:

- Amazon VPC.
- Amazon EC2.
- Amazon RDS.
- Amazon S3.
- Amazon SQS.
- AWS Lambda.
- Amazon SES.
- Amazon Location Service.
- AWS Secrets Manager.

---

## 3. AWS Access Permissions

The AWS account, IAM user, or IAM role used during the workshop must have permission to create, update, and delete the required resources.

The main services that require access permissions include:

- Amazon VPC.
- Amazon EC2.
- Elastic Load Balancing.
- Amazon EC2 Auto Scaling.
- Amazon RDS.
- AWS Secrets Manager.
- Amazon S3.
- Amazon SQS.
- AWS Lambda.
- Amazon SES.
- Amazon Location Service.
- AWS IAM.
- AWS Systems Manager.
- Amazon CloudWatch.
- AWS KMS.

When using an IAM user or a restricted IAM role, ensure that the principal has sufficient permissions to complete the labs.

In production environments, always follow the **principle of least privilege**.

---

## 4. Required Tools

Prepare the following tools on your computer:

- A modern web browser.
- Visual Studio Code.
- Git.
- AWS CLI.
- Terminal, PowerShell, or Git Bash.
- A tool for extracting `.zip` or `.tar.gz` archives.

These tools are used to:

- Manage source code.
- Edit configuration files.
- Run AWS CLI commands.
- Upload deployment packages to Amazon S3.
- Manage release files.
- Build and maintain the workshop report website.

Verify the AWS CLI installation by running:

```bash
aws --version
```

---

## 5. Configure AWS CLI

After installing AWS CLI, configure your AWS credentials by running:

```bash
aws configure
```

Enter the required information:

```text
AWS Access Key ID
AWS Secret Access Key
Default region name: ap-southeast-1
Default output format: json
```

Do not store access keys directly in source code or files committed to GitHub.

For the Amazon EC2 instances used in this workshop, the application uses an IAM Instance Profile instead of storing access keys on the server.

---

## 6. Source Code and Deployment Package

Prepare the source code or application release package for the Delivery Management System.

The sample deployment package used in the workshop is:

```text
WedNightFury-linux-x64-v9.tar.gz
```

After deployment, the application runs from:

```text
/opt/delivery/current/WedNightFury
```

The application is managed by the following systemd service:

```text
delivery.service
```

The release package is stored in Amazon S3 and downloaded to the EC2 instance during deployment.

Example storage location:

```text
s3://delivery-dev-pod-nm2026a/deployments/
```

---

## 7. Resource Naming Convention

To avoid confusion during the workshop, use consistent names for the AWS resources.

| Resource | Name |
|---|---|
| VPC | `delivery-dev-vpc` |
| EC2 Security Group | `delivery-ec2-sg` |
| ALB Security Group | `delivery-alb-sg` |
| EC2 IAM Role | `delivery-ec2-role` |
| Launch Template | `delivery-ec2-lt` |
| Target Group | `delivery-app-tg` |
| Application Load Balancer | `delivery-alb` |
| Application Service | `delivery.service` |

Use these names consistently so that the configuration remains aligned across all labs.

---

## 8. Prepare EC2 Administration with AWS Systems Manager

The application EC2 instances are deployed in private application subnets and do not require public IP addresses.

Instance administration is performed through **AWS Systems Manager Session Manager**.

To use Session Manager successfully, ensure that:

- The EC2 instance has an appropriate IAM Instance Profile.
- The IAM role includes the required Systems Manager permissions.
- The SSM Agent is installed and running on the selected AMI.
- The EC2 instance has outbound connectivity through a NAT Gateway or suitable VPC Endpoints.
- The instance appears in the Systems Manager Managed Nodes list.

This method avoids exposing SSH access directly to the Internet.

---

## 9. Prepare an Email Address for Amazon SES

The workshop uses **Amazon Simple Email Service (Amazon SES)** to send notification emails.

Before testing, prepare an active email address that can be used to:

- Create an email identity.
- Receive the Amazon SES verification message.
- Send and receive test emails.
- Verify the notification function of the application.

When the Amazon SES account is still in the Sandbox environment, both the sender and recipient addresses may need to be verified.

---

## 10. Review Service Quotas and Costs

Before starting the workshop, review:

- Amazon EC2 service quotas.
- Elastic IP address quotas.
- NAT Gateway quotas.
- Amazon RDS quotas.
- Amazon SES account status.
- Amazon Location Service availability.
- The expected Auto Scaling Group budget.

You may create an AWS Budget or a CloudWatch billing alarm to monitor costs.

---

## 11. Verify the Environment

Before continuing to the first lab, confirm that:

- You can sign in to the AWS Management Console.
- The selected Region is `ap-southeast-1`.
- AWS CLI is installed and working correctly.
- Your AWS account has sufficient permissions.
- Visual Studio Code, Git, and a terminal are available.
- The application source code or deployment package is ready.
- An email address is available for Amazon SES testing.
- AWS Systems Manager is accessible.
- You understand the workshop resource naming convention.
- You understand which resources may incur charges.

---

## Results

After completing the prerequisites, you have:

- Prepared the AWS account and access permissions.
- Selected the correct deployment Region.
- Installed the required tools.
- Configured AWS CLI.
- Prepared the source code and deployment package.
- Prepared EC2 administration through Session Manager.
- Prepared an email address for Amazon SES testing.
- Completed the requirements for starting the infrastructure deployment.

---

Are you ready?

After completing these prerequisites, we will begin **Lab 1: Network Infrastructure**, where the system VPC, subnets, Internet Gateway, NAT Gateway, and Route Tables will be deployed.