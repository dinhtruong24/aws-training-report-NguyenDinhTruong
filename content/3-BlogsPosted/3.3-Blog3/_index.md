---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---


# UNDERSTANDING VPC LINKS IN AMAZON API GATEWAY PRIVATE INTEGRATIONS

Modern cloud applications often keep backend services inside an Amazon VPC to improve security and prevent direct Internet access. However, applications still need a secure way for users to communicate with these private services. Amazon API Gateway VPC Link provides a secure connection between API Gateway and backend resources running inside a VPC, allowing organizations to expose APIs without exposing their infrastructure.

## Overview

Amazon API Gateway VPC Link enables private integrations between API Gateway and backend applications hosted in Amazon EC2, Amazon ECS, Amazon EKS, or other services inside an Amazon VPC. Instead of allowing clients to access backend resources directly, API Gateway forwards requests through a private network connection, improving both security and network isolation.

## Solution Architecture

Depending on the API type, Amazon API Gateway supports different VPC Link architectures.

### REST API VPC Link

REST APIs use AWS PrivateLink together with a Network Load Balancer (NLB) to establish a private connection between API Gateway and backend services inside the VPC. This architecture is suitable for traditional REST-based applications that require secure access to internal resources.

### Private APIs with Private Integrations

Private APIs can only be accessed from authorized Amazon VPCs through Interface VPC Endpoints. When combined with VPC Link, both the API endpoint and backend services remain private, providing an additional layer of network security for internal enterprise applications.

### HTTP API VPC Link

HTTP APIs use AWS Hyperplane technology instead of AWS PrivateLink. This approach supports multiple integration targets such as Application Load Balancers (ALB), Network Load Balancers (NLB), and AWS Cloud Map services. Compared with REST APIs, HTTP APIs provide simpler configuration, lower latency, and reduced operational costs.

## Implementation Workflow

The deployment process consists of five main steps.

### Step 1 – Deploy Backend Services

Deploy the application on Amazon EC2, Amazon ECS, or Amazon EKS inside private subnets.

### Step 2 – Configure a Load Balancer

Create an Application Load Balancer or Network Load Balancer to receive traffic from API Gateway.

### Step 3 – Create a VPC Link

Configure a VPC Link in Amazon API Gateway and associate it with the selected load balancer.

### Step 4 – Configure API Gateway

Create API routes and integrate them with the VPC Link so that requests are securely forwarded to backend services.

### Step 5 – Test the Connection

Verify that requests sent to API Gateway successfully reach the backend application while maintaining private network communication.

## Benefits

Amazon API Gateway VPC Link provides several important advantages:

- Keeps backend services private.
- Prevents direct Internet access.
- Improves network security.
- Supports REST APIs and HTTP APIs.
- Integrates with ALB, NLB, and AWS Cloud Map.
- Simplifies private API deployment.
- Supports scalable and highly available architectures.
- Reduces operational complexity.

## Conclusion

Amazon API Gateway VPC Link is an effective solution for securely connecting APIs with backend services inside an Amazon VPC. Whether using REST APIs with AWS PrivateLink or HTTP APIs with AWS Hyperplane, organizations can protect internal applications while providing secure and scalable API access for users.

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog3-rest-api.png" width="700">
</p>

<p align="center">
<i>Figure 3.1. Architecture of VPC Link for Amazon API Gateway REST APIs.</i>
</p>

<br>

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog3-private-api.png" width="700">
</p>

<p align="center">
<i>Figure 3.2. Private API architecture using private integrations.</i>
</p>

<br>

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog3-http-api.png" width="700">
</p>

<p align="center">
<i>Figure 3.3. Architecture of VPC Link for Amazon API Gateway HTTP APIs.</i>
</p>

---

<p align="center">
<strong>Reference Article:</strong>
<a href="https://aws.amazon.com/blogs/compute/understanding-vpc-links-in-amazon-api-gateway-private-integrations/">
AWS Compute Blog
</a>
</p>

<p align="center">
<strong>Community Post:</strong>
<a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2194084638023163">
AWS Study Group – Facebook
</a>
</p>