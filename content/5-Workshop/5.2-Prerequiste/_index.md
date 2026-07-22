---
title : "Prerequisites"
date : 2024-01-01 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

To successfully deploy the **VietAI Scholar Assistant** system, you need to prepare the AWS environment and the required development tools. Completing the following prerequisites will help ensure a smooth deployment process and minimize potential issues during implementation.

## 1. AWS Account

You need an active AWS account to create and manage the AWS services used throughout this workshop.

It is recommended to use the **AWS Free Tier** if you are new to AWS. In addition, make sure your account has been fully activated and has permission to create the required AWS resources.

---

## 2. Select an AWS Region

Throughout this workshop, all resources will be deployed in the same AWS Region to ensure that AWS services can communicate with each other properly.

Recommended Region:

- **Asia Pacific (Singapore) – ap-southeast-1**

Using the same Region helps reduce network latency and prevents connection issues between AWS services.

---

## 3. Development Tools

Your computer should have the following development tools installed:

- Visual Studio Code
- Git
- Python 3.11 or later
- Node.js
- AWS CLI
- Docker Desktop (recommended)

These tools will be used throughout the process of building and deploying the system.

---

## 4. AWS Permissions

Make sure your AWS account has permission to access the following services:

- Amazon S3
- AWS Lambda
- Amazon Bedrock
- Amazon DynamoDB
- Amazon Cognito
- Amazon API Gateway
- AWS Identity and Access Management (IAM)
- Amazon CloudFront
- Amazon CloudWatch

If you are using an IAM user, ensure that the required permissions have been granted before starting the workshop.

---

## 5. Amazon Bedrock Access

This project uses **Amazon Bedrock** to build AI Agents and process documents.

Before starting the labs, verify that your AWS account has access to Amazon Bedrock and the language models that will be used throughout the workshop.

---

## 6. Project Source Code

Prepare the **VietAI Scholar Assistant** project source code on your local machine and verify that all required dependencies have been installed.

If you are using Git, clone the project repository before starting the deployment.

---

## 7. Environment Verification

Before proceeding to the first lab, make sure that:

- You can successfully sign in to the AWS Management Console.
- The correct AWS Region has been selected.
- AWS CLI is working properly.
- All required development tools have been installed.
- You can access the required AWS services.

---

Are you ready?

After completing all the prerequisites above, we will begin **Lab 1: Document Storage & Upload**, where the system starts by storing and managing documents in Amazon S3.