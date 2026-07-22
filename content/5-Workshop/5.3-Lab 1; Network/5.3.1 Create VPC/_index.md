---
title : "Create an Amazon S3 Bucket"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.3.1. </b> "
---

# CREATE AN AMAZON S3 BUCKET

In this section, we will create an **Amazon S3 Bucket** to store PDF documents for the **VietAI Scholar Assistant** system. The bucket will serve as the storage location for input documents, processed data, and AI-generated outputs used throughout the following labs.

---

## Step 1. Create an Amazon S3 Bucket

Sign in to the **AWS Management Console**, search for the **Amazon S3** service, and select **Create bucket**.

Enter a unique bucket name that follows Amazon S3 naming conventions, choose the **Asia Pacific (Singapore) – ap-southeast-1** Region, keep the default settings for **Object Ownership**, **Block Public Access**, and **Default Encryption**, then click **Create bucket** to complete the bucket creation process.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-create-s3-bucket.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.1. Creating an Amazon S3 Bucket in the AWS Management Console.</i>
</p>

---

## Step 2. Create the document storage structure

After the bucket has been created successfully, open the newly created bucket and select **Create folder** to create the folders required by the system.

For the **VietAI Scholar Assistant** project, create the following three folders:

```text
uploads/
processed/
outputs/
```

Where:

- **uploads/**: Stores PDF documents uploaded by users.
- **processed/**: Stores data after OCR and other preprocessing steps have been completed.
- **outputs/**: Stores the final results, such as summaries, translations, and AI-generated content.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-create-folder.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.2. Creating logical folders inside the Amazon S3 Bucket.</i>
</p>

---

## Expected Result

After completing this section, the system will have an **Amazon S3 Bucket** configured in the correct AWS Region together with the initial document storage structure. This storage environment will provide the foundation for AI services to access and process documents in the subsequent labs.

Next, we will proceed to **5.3.2 – Configure Document Upload** to configure the document upload workflow from the application to Amazon S3.