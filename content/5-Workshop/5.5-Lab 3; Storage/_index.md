---
title : "Lab 3: Amazon S3 Storage"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b>5.5. </b> "
---

In this lab, we will deploy **Amazon Simple Storage Service (Amazon S3)** as the storage solution for the system.

Amazon S3 is a highly durable, scalable object storage service that integrates seamlessly with many AWS services. In this project, Amazon S3 is used to store documents, images, and files uploaded by users.

Besides creating an S3 Bucket and organizing its folder structure, we will also configure an **S3 Gateway Endpoint** so that resources inside the VPC can access Amazon S3 without using the public Internet. This approach improves security while reducing data transfer costs.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.5-lab3/5.5.1-create-s3-bucket.png" width="900">
</p>

<p align="center">
<i>Figure 5.5.1. Creating the Amazon S3 Bucket for the system.</i>
</p>

---

## Lab Objectives

After completing this lab, you will be able to:

- Create an Amazon S3 Bucket.
- Configure the folder structure inside the bucket.
- Manage application data stored in Amazon S3.
- Configure an S3 Gateway Endpoint.
- Allow EC2 instances to access Amazon S3 through the AWS private network.
- Reduce Internet traffic by using a Gateway Endpoint.
- Prepare the storage environment for the following labs.

---

## Storage Architecture

In this lab, the storage architecture is organized as follows:

```text
Application
      │
      ▼
Amazon S3 Bucket
      │
      ├── documents/
      ├── uploads/
      └── backups/
```

The EC2 instances will access Amazon S3 directly through the **S3 Gateway Endpoint** without using an Internet Gateway or NAT Gateway.

---

## Main Components

This lab uses the following AWS services and resources:

| Component | Description |
|---|---|
| Amazon S3 | Stores application data |
| S3 Bucket | Stores all application files |
| Folder Structure | Organizes files into logical directories |
| S3 Gateway Endpoint | Provides private access to Amazon S3 from the VPC |

---

## Lab Contents

Lab 3 is divided into three sections:

### 5.5.1 Create an Amazon S3 Bucket

In this section, we will:

- Create a new S3 Bucket.
- Configure the AWS Region.
- Configure the basic bucket settings.
- Verify that the bucket has been created successfully.

### 5.5.2 Create the Folder Structure

In this section, we will:

- Create folders inside the S3 Bucket.
- Prepare the storage locations for application data.
- Verify the folder structure.

### 5.5.3 Configure the S3 Gateway Endpoint

In this section, we will:

- Create an S3 Gateway Endpoint.
- Associate the endpoint with the appropriate Route Table.
- Allow EC2 instances to access Amazon S3 through the AWS private network.
- Verify the connectivity between EC2 and Amazon S3.

---

## Expected Results

After completing Lab 3:

- The Amazon S3 Bucket has been created successfully.
- The folder structure inside the bucket has been configured.
- The S3 Gateway Endpoint has been created successfully.
- EC2 instances can access Amazon S3 without using the Internet.
- The system has a secure and efficient storage environment.

After completing Lab 3, the environment will be ready for **Lab 4 – CloudWatch Monitoring**.