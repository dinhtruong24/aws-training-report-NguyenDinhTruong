---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# SECURING DATABASE CREDENTIALS FOR AWS LAMBDA WITH AWS SECRETS MANAGER

Managing database credentials securely is an important requirement when building serverless applications. Hardcoding usernames and passwords inside AWS Lambda functions increases security risks and makes credential management difficult. AWS Secrets Manager provides a secure solution for storing, retrieving, and automatically rotating database credentials.

## Overview

AWS Secrets Manager enables applications to retrieve database credentials only when they are needed. Instead of embedding sensitive information inside source code or environment variables, Lambda securely requests the secret during runtime, reducing the risk of credential exposure.

## Solution Architecture

The solution integrates several AWS services:

- Amazon API Gateway receives client requests.
- AWS Lambda processes application logic.
- AWS Secrets Manager stores database credentials securely.
- Amazon RDS provides the backend database.

This architecture keeps sensitive information outside the application source code while allowing Lambda to access credentials securely.

## Implementation Workflow

The solution follows four main steps.

### Step 1 – Store Credentials

Create a secret in AWS Secrets Manager containing the Amazon RDS username and password.

### Step 2 – Configure AWS Lambda

Grant Lambda permission to retrieve the secret using an IAM Role.

### Step 3 – Retrieve the Secret

When Lambda executes, it requests the database credentials from AWS Secrets Manager and establishes a secure connection to Amazon RDS.

### Step 4 – Enable Automatic Rotation

AWS Secrets Manager automatically rotates database credentials based on a predefined schedule without requiring application changes.

## Benefits

Using AWS Secrets Manager provides several advantages:

- Removes hardcoded passwords from source code.
- Protects sensitive credentials securely.
- Supports automatic credential rotation.
- Simplifies credential management.
- Improves security for serverless applications.
- Integrates seamlessly with AWS services.

## Conclusion

AWS Secrets Manager is an effective solution for managing database credentials in serverless applications. By combining API Gateway, Lambda, Secrets Manager, and Amazon RDS, developers can improve security, reduce operational overhead, and simplify credential management.

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog1-architecture.png" width="700" alt="AWS Secrets Manager Architecture">
</p>

<p align="center">
<i>Figure 1. Architecture for securely managing Amazon RDS database credentials using AWS Secrets Manager.</i>
</p>

<p align="center">
<strong>Reference Article:</strong>
<a href="https://aws.amazon.com/blogs/security/how-to-securely-provide-database-credentials-to-lambda-functions-by-using-aws-secrets-manager/">
AWS Security Blog
</a>
</p>

<p align="center">
<strong>Community Post:</strong>
<a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2187144322050528">
AWS Study Group – Facebook
</a>
</p>