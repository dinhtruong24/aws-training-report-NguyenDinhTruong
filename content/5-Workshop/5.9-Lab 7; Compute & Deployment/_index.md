---
title : "Lab 7: Compute & Deployment"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b>5.9. </b> "
---

In this lab, we will deploy the compute infrastructure and configure the required AWS services to provide a scalable and highly available environment for the application.

We will use **Amazon EC2**, **Application Load Balancer (ALB)**, and **Amazon EC2 Auto Scaling** to build the deployment environment. This architecture distributes incoming traffic across multiple EC2 instances while automatically scaling compute resources based on application demand.

In this lab, we will create a **Launch Template**, **Target Group**, **Application Load Balancer**, and **Auto Scaling Group** to complete the deployment environment.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-create-launch-template.png" width="900">
</p>

<p align="center">
<i>Figure 5.9.1. Creating a Launch Template.</i>
</p>

---

## Lab Objectives

After completing this lab, you will be able to:

- Create an EC2 Launch Template.
- Create a Target Group.
- Configure an Application Load Balancer.
- Create an Auto Scaling Group.
- Prepare a scalable deployment environment.

---

## Deployment Architecture

The deployment architecture used in this lab is shown below:

```text
Internet
     │
     ▼
Application Load Balancer
     │
     ▼
Target Group
     │
     ▼
Auto Scaling Group
     │
     ▼
Amazon EC2 Instances
```

The Application Load Balancer distributes incoming requests across multiple EC2 instances managed by the Auto Scaling Group, improving application availability and scalability.

---

## Main Components

This lab uses the following AWS services:

| Component | Description |
|---|---|
| Amazon EC2 | Virtual servers for hosting the application |
| Launch Template | EC2 instance configuration template |
| Target Group | Collection of targets for the load balancer |
| Application Load Balancer | Distributes incoming application traffic |
| Auto Scaling Group | Automatically scales EC2 instances |

---

## Lab Contents

Lab 7 consists of four sections:

### 5.9.1 Create Launch Template

In this section, we will:

- Create a Launch Template.
- Configure the AMI, Instance Type, and Security Group.

### 5.9.2 Create Target Group

In this section, we will:

- Create a Target Group.
- Configure Health Checks.

### 5.9.3 Create Application Load Balancer

In this section, we will:

- Create an Application Load Balancer.
- Associate it with the Target Group.

### 5.9.4 Create Auto Scaling Group

In this section, we will:

- Create an Auto Scaling Group.
- Associate it with the Launch Template and Load Balancer.
- Verify automatic scaling functionality.

---

## Expected Results

After completing Lab 7:

- A Launch Template has been created successfully.
- A Target Group has been configured.
- The Application Load Balancer is operating correctly.
- An Auto Scaling Group has been deployed.
- A scalable and highly available deployment environment has been established.

After completing Lab 7, the system is ready for the **End-to-End Testing** phase in the next section.