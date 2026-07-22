---
title : "Create an Amazon S3 Bucket"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.5.1. </b> "
---

In this section, we will create an **Amazon S3 Bucket** to store the application's data.

The Amazon S3 Bucket serves as the centralized storage location for documents, images, and files uploaded by users. The bucket is created in the same AWS Region as the other system resources to reduce latency and improve overall performance.

---

## Step 1. Open the Amazon S3 Service

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Search for **Amazon S3**.
2. Select **Buckets**.
3. Click **Create bucket**.

---

## Step 2. Configure the S3 Bucket

On the **Create bucket** page, enter the following information:

**Bucket name**

```text
delivery-dev-storage
```

**AWS Region**

```text
Asia Pacific (Singapore) – ap-southeast-1
```

Keep the default settings for:

- Object Ownership
- Block Public Access
- Bucket Versioning
- Default Encryption

After completing the configuration, click **Create bucket**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.5-lab3/5.5.1-create-s3-bucket.png" width="900">
</p>

<p align="center">
<i>Figure 5.5.2. Creating the Amazon S3 Bucket.</i>
</p>

---

## Step 3. Verify the S3 Bucket

After the bucket has been created successfully:

- Open the **Buckets** list.
- Verify that the new bucket appears.
- Confirm the bucket Region.
- Verify that the bucket status is normal.

The bucket will be used in the following sections to store application data.

---

## Configuration Summary

| Property | Value |
|---|---|
| AWS Service | Amazon S3 |
| Bucket Name | `delivery-dev-storage` |
| Region | Asia Pacific (Singapore) |
| Versioning | Disabled |
| Block Public Access | Enabled |
| Default Encryption | AWS Managed Keys (SSE-S3) |

---

## Result

After completing this section, you have successfully:

- Created an Amazon S3 Bucket.
- Configured the bucket in the appropriate AWS Region.
- Kept the default security settings.
- Prepared the storage environment for the application.
- Completed the initial Amazon S3 configuration.

In the next section, we will continue with **5.5.2 – Create the Folder Structure**.