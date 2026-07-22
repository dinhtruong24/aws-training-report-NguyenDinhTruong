---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### Overview

This workshop guides you through deploying a **Delivery Management System on AWS** using a secure, scalable, and highly available cloud architecture.

Throughout the workshop, you will build the complete infrastructure step by step, including networking, security configuration, database deployment, Amazon S3 storage, event processing with Amazon SQS and AWS Lambda, email notification with Amazon SES, integration with Amazon Location Service, and application deployment on Amazon EC2 behind an Application Load Balancer.

The system follows a multi-tier architecture consisting of public subnets, private application subnets, and private database subnets. The Application Load Balancer receives incoming traffic from the Internet, Amazon EC2 instances host the application within private subnets, and Amazon RDS for MySQL stores application data inside private database subnets.

In addition, this workshop demonstrates how to deploy applications using symbolic links, perform health checks, roll back failed releases, execute end-to-end testing, and clean up AWS resources after the deployment is complete.

---

#### Architecture Highlights

- **Networking:** Amazon VPC is divided into public subnets, private application subnets, and private database subnets across multiple Availability Zones.
- **Load Balancing:** An Application Load Balancer receives Internet traffic and forwards requests to the Target Group.
- **Compute:** Amazon EC2 hosts the delivery management application and is managed by an Auto Scaling Group.
- **Database:** Amazon RDS for MySQL stores application data within private database subnets.
- **Secrets Management:** AWS Secrets Manager securely stores database credentials, eliminating the need to hard-code sensitive information in the application.
- **Storage:** Amazon S3 stores Proof of Delivery (POD) images, driver signatures, failed delivery evidence, and application deployment packages.
- **Messaging:** Amazon SQS receives order-related events and supports asynchronous message processing.
- **Serverless Processing:** AWS Lambda processes SQS events and executes background tasks.
- **Email:** Amazon SES is used to send email notifications.
- **Location Services:** Amazon Location Service provides geolocation and location search capabilities.
- **Security:** AWS IAM, Security Groups, and IAM Instance Profiles manage access control and secure AWS resources.
- **Deployment:** The application is deployed on Amazon EC2 using release directories and symbolic links, enabling fast deployments and rollback.
- **High Availability:** Application Load Balancer and Auto Scaling Group improve system availability and scalability.

---

#### Contents

1. [Workshop Overview]({{< relref "5.1-Workshop-overview" >}})
2. [Prerequisites]({{< relref "/5-Workshop/5.2-Prerequisite/_index.md" >}})
3. [Lab 1: Network Infrastructure]({{< relref "5.3-Lab 1; Network" >}})
4. [Lab 2: Security Groups and IAM]({{< relref "5.4-Lab 2; Security" >}})
5. [Lab 3: Storage with Amazon S3]({{< relref "5.5-Lab 3; Storage" >}})
6. [Lab 4: Database and Related Services]({{< relref "5.6-Lab 4; Database" >}})
7. [Lab 5: Events, Lambda, and Email]({{< relref "5.7-Lab 5; Event-Driven Services" >}})
8. [Lab 6: Amazon Location Service]({{< relref "5.8-Lab 6; Amazon Location Service" >}})
9. [Lab 7: Compute & Deployment]({{< relref "5.9-Lab 7; Compute & Deployment" >}})
10. [End-to-End Testing]({{< relref "5.10-End-to-End Testing" >}})
11. [Cleanup]({{< relref "5.11-Cleanup" >}})

---

## Learning Objectives

After completing this workshop, you will be able to:

- Design an Amazon VPC with public subnets, private application subnets, and private database subnets.
- Configure Internet Gateway, Route Tables, and NAT Gateway.
- Build a Security Group architecture for the Application Load Balancer, Amazon EC2, and Amazon RDS.
- Create IAM Roles and Instance Profiles for Amazon EC2 following the principle of least privilege.
- Store application data using Amazon S3.
- Deploy Amazon RDS for MySQL in private database subnets.
- Use AWS Secrets Manager to manage database credentials securely.
- Configure Amazon SQS and AWS Lambda for asynchronous event processing.
- Send email notifications using Amazon SES.
- Integrate Amazon Location Service into the application.
- Create a Launch Template, Target Group, Application Load Balancer, and Auto Scaling Group.
- Deploy application releases from Amazon S3 using symbolic links.
- Perform health checks and roll back failed deployments.
- Validate the complete system through end-to-end testing.
- Clean up AWS resources to avoid unnecessary charges.

---

## System Architecture

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/Workshop.png" width="900">
</p>