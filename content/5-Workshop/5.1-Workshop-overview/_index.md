---
title : "Workshop Overview"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

## Introduction

In this workshop, we will deploy a **Delivery Management System on AWS** using a secure, scalable, and highly available multi-tier architecture.

The system supports delivery operations by managing orders, users, distribution centers, shipment status, Proof of Delivery (POD) images, driver signatures, and failed delivery evidence.

The application is deployed on **Amazon EC2** behind an **Application Load Balancer**. The EC2 instances run inside private application subnets, while **Amazon RDS for MySQL** is deployed in private database subnets to prevent direct access from the Internet.

In addition, the system uses **Amazon S3** to store files and images, **Amazon SQS** for asynchronous order events, **AWS Lambda** for background processing, **Amazon SES** for email notifications, and **Amazon Location Service** for geolocation and location search capabilities.

---

## Workshop Objectives

After completing this workshop, you will be able to:

- Design an Amazon VPC with public subnets, private application subnets, and private database subnets.
- Configure an Internet Gateway, NAT Gateway, and Route Tables.
- Build a Security Group architecture for the Application Load Balancer, Amazon EC2, and Amazon RDS.
- Create IAM Roles and Instance Profiles for Amazon EC2 following the principle of least privilege.
- Deploy Amazon RDS for MySQL within private database subnets.
- Use AWS Secrets Manager to securely manage database credentials.
- Store POD images, driver signatures, and failed delivery evidence in Amazon S3.
- Process asynchronous events using Amazon SQS and AWS Lambda.
- Send email notifications through Amazon SES.
- Integrate Amazon Location Service into the application.
- Create a Launch Template, Target Group, Application Load Balancer, and Auto Scaling Group.
- Deploy application releases using symbolic links.
- Perform health checks, rollback failed deployments, and validate the complete system.

---

## System Architecture

The system is built using a secure multi-tier AWS architecture.

Users access the application through the **Application Load Balancer**, which distributes incoming requests to healthy Amazon EC2 instances registered in the **Target Group**.

The Amazon EC2 instances run inside private application subnets without public IP addresses. Administrative access is provided through **AWS Systems Manager Session Manager**, eliminating the need to expose SSH access to the Internet.

The application retrieves database credentials from **AWS Secrets Manager** and connects securely to **Amazon RDS for MySQL** hosted in private database subnets.

Application files, including POD images, driver signatures, failed delivery evidence, and deployment packages, are stored in **Amazon S3**. Order-related events are sent to **Amazon SQS**, where **AWS Lambda** processes the messages and can send notification emails through **Amazon SES**.

**Amazon Location Service** provides geocoding, reverse geocoding, and location search capabilities for the application.

---

## Main Processing Flow

```text
User
  │
  ▼
Application Load Balancer
  │
  ▼
Target Group
  │
  ▼
Amazon EC2
  │
  ├── AWS Secrets Manager
  │        │
  │        ▼
  │   Amazon RDS MySQL
  │
  ├── Amazon S3
  │
  ├── Amazon SQS
  │        │
  │        ▼
  │    AWS Lambda
  │        │
  │        ▼
  │    Amazon SES
  │
  └── Amazon Location Service
```

---

## AWS Services Used

This workshop uses the following AWS services:

- Amazon VPC
- Internet Gateway
- NAT Gateway
- Amazon EC2
- Amazon EC2 Auto Scaling
- Application Load Balancer
- Amazon RDS for MySQL
- AWS Secrets Manager
- Amazon S3
- Amazon SQS
- AWS Lambda
- Amazon SES
- Amazon Location Service
- AWS IAM
- AWS Systems Manager
- AWS KMS

Each service plays a specific role in providing scalability, security, reliable storage, and efficient application processing throughout the system.

---

## Knowledge Gained

After completing this workshop, you will understand:

- How to design a secure multi-tier network architecture on Amazon VPC.
- How to separate public, private application, and private database subnets.
- How to configure Security Groups for Application Load Balancer, Amazon EC2, and Amazon RDS.
- How to use IAM Roles instead of static access keys.
- How to deploy applications on Amazon EC2 within private subnets.
- How to store application data and files in Amazon S3.
- How to manage Amazon RDS for MySQL and AWS Secrets Manager.
- How to process asynchronous events using Amazon SQS and AWS Lambda.
- How to send email notifications using Amazon SES.
- How to integrate Amazon Location Service into an application.
- How to deploy applications behind an Application Load Balancer.
- How to configure an Auto Scaling Group.
- How to deploy new releases using symbolic links and perform rollback when necessary.
- How to perform end-to-end testing and clean up AWS resources after deployment.

---

## Overall Architecture

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.1-Workshop-overview/overview5.1.png" width="1000">
</p>

<p align="center">
<i>Figure 5.1. Overall architecture of the Delivery Management System deployed on AWS.</i>
</p>

---

After completing the **Workshop Overview**, we will continue by preparing the AWS account, required permissions, development tools, and other prerequisites in the **Prerequisites** section.