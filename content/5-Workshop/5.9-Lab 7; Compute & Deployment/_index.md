---
title : "Lab 7: Compute & Deployment"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b>5.9. </b> "
---

In this lab, we will deploy the delivery management application on **Amazon EC2** and configure the infrastructure required to provide load balancing, scalability, and reliable application deployment.

The environment uses an EC2 Launch Template, a Target Group, an Application Load Balancer, and an Auto Scaling Group. The application instances run in private application subnets and are managed through **AWS Systems Manager Session Manager** instead of direct SSH access.

This lab also introduces a release deployment process based on symbolic links. This approach allows a new application version to be activated quickly and enables rollback to the previous release when an error occurs.

---

## Lab Objectives

After completing this lab, you will be able to:

- Create an EC2 Launch Template for the application.
- Configure a Target Group on HTTP port `5000`.
- Create an Internet-facing Application Load Balancer.
- Configure an Auto Scaling Group in private application subnets.
- Deploy an application release from Amazon S3.
- Update the active release by changing a symbolic link.
- Verify the application service and HTTP health status.
- Roll back to the previous release when deployment fails.

---

## Deployment Architecture

The application deployment flow is organized as follows:

```text
Internet
    │
    ▼
Application Load Balancer
    │
    ▼
Target Group
HTTP:5000
    │
    ▼
Auto Scaling Group
    │
    ▼
Amazon EC2 Instances
Private Application Subnets
    │
    ▼
delivery.service
/opt/delivery/current/WedNightFury
```

The Application Load Balancer receives requests from users and forwards them to healthy EC2 instances registered with the Target Group.

The EC2 instances are created from the Launch Template and managed by the Auto Scaling Group. Each instance runs the application through the `delivery.service` systemd service.

---

## Main Components

| Component | Recommended configuration |
|---|---|
| Launch Template | Appropriate AMI, `delivery-ec2-role`, `delivery-ec2-sg`, and configured root volume |
| Target Group | HTTP port `5000` with `/` or a dedicated health-check endpoint |
| Application Load Balancer | Internet-facing, deployed in `public-a` and `public-b`, using `delivery-alb-sg` |
| Auto Scaling Group | Deployed in `app-a` and `app-b`; minimum 1, desired 1, maximum based on the workshop budget |
| EC2 Service | `delivery.service` |
| Application Executable | `/opt/delivery/current/WedNightFury` |
| Instance Management | AWS Systems Manager Session Manager |

---

## Lab Contents

Lab 7 consists of four sections. The existing section names are retained in the website structure.

### 5.9.1 Create Launch Template

In this section, we will:

- Create the `delivery-ec2-lt` Launch Template.
- Select an appropriate Amazon Machine Image.
- Attach the `delivery-ec2-role` instance profile.
- Configure the `delivery-ec2-sg` Security Group.
- Configure the root storage volume.
- Prepare EC2 instances for deployment in private application subnets.

### 5.9.2 Create Target Group

In this section, we will:

- Create the `delivery-app-tg` Target Group.
- Configure HTTP traffic on port `5000`.
- Configure the application health check.
- Prepare the Target Group for integration with the Application Load Balancer.

### 5.9.3 Create Application Load Balancer

In this section, we will:

- Create the Internet-facing `delivery-alb`.
- Deploy the Load Balancer in the two public subnets.
- Attach the `delivery-alb-sg` Security Group.
- Forward incoming traffic to `delivery-app-tg`.
- Deploy a new application release from Amazon S3 using symbolic links.

### 5.9.4 Create Auto Scaling Group

In this section, we will:

- Create an Auto Scaling Group using `delivery-ec2-lt`.
- Deploy application instances in `app-a` and `app-b`.
- Configure the minimum, desired, and maximum capacities.
- Verify `delivery.service` and the application HTTP response.
- Review application logs.
- Roll back to the previous release if the new release fails.

---

## Release Deployment Workflow

The application release is downloaded from Amazon S3 and extracted into a version-specific release directory.

The `/opt/delivery/current` symbolic link is then updated to point to the new release before restarting `delivery.service`.

```text
Amazon S3 deployment package
             │
             ▼
/opt/delivery/packages/
             │
             ▼
/opt/delivery/releases/{RELEASE}
             │
             ▼
/opt/delivery/current
             │
             ▼
delivery.service
```

When a release does not include database schema changes, migrations should not be executed unnecessarily.

---

## Health Check and Rollback

After deployment, the following items must be verified:

- The `/opt/delivery/current` symbolic link points to the expected release.
- `delivery.service` is running successfully.
- The local application endpoint on port `5000` returns HTTP `200`.
- Recent application logs do not contain deployment errors.
- The Target Group reports the EC2 instance as healthy.

If the new release fails, the symbolic link can be restored to the previous release and the service can be restarted.

---

## Expected Results

After completing Lab 7:

- The EC2 Launch Template has been configured successfully.
- The Target Group accepts application traffic on port `5000`.
- The Application Load Balancer forwards requests to healthy instances.
- The Auto Scaling Group manages the application instances in private subnets.
- The application runs through `delivery.service`.
- New releases can be deployed using the symbolic-link strategy.
- The previous release can be restored quickly if deployment fails.
- The system is ready for end-to-end testing.