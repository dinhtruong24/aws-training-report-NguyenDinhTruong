---
title : "Configure Amazon S3 Access and Connectivity"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.3.2. </b> "
---

# CONFIGURE AMAZON S3 ACCESS AND CONNECTIVITY

In this section, we will configure Amazon S3 access so that the components of the **VietAI Scholar Assistant** system can securely store and retrieve documents. We will also verify the connectivity between the application and Amazon S3 before proceeding to the AI document processing stages.

---

## Step 1. Configure Amazon S3 Access

After creating the Amazon S3 Bucket, configure the required access permissions so that the application can read and write data stored in Amazon S3. The required permissions include:

- `s3:ListBucket`
- `s3:GetObject`
- `s3:PutObject`
- `s3:DeleteObject`

These permissions should only be granted to the project Bucket in accordance with the **Principle of Least Privilege**, ensuring secure and controlled access to stored documents.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2%20Configure%20Amazon%20S3%20Access.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.3. Configuring Amazon S3 access permissions.</i>
</p>

---

## Step 2. Upload Documents to Amazon S3

After the access permissions have been configured, open the Amazon S3 Bucket created in the previous step and select **Upload** to upload documents.

For the **VietAI Scholar Assistant** project, PDF documents are stored in the **uploads/** folder and serve as the primary input for the OCR, Retrieval-Augmented Generation (RAG), and Generative AI processing stages implemented later in the workshop.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2%20Upload%20Documents.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.4. Uploading PDF documents to the Amazon S3 Bucket.</i>
</p>

---

## Step 3. Verify Amazon S3 Connectivity

After the documents have been uploaded successfully, verify the connectivity between the application and Amazon S3 to ensure that stored documents can be accessed correctly.

This verification confirms that the Bucket has been configured properly and is ready to support the AI-powered document processing workflow in the following workshop modules.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2%20Configure%20S3%20Connectivity.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.5. Verifying connectivity to Amazon S3.</i>
</p>

---

## Expected Results

After completing this section:

- Amazon S3 access permissions have been configured successfully.
- The Bucket is ready to store and manage project documents.
- Documents have been uploaded successfully to Amazon S3.
- Connectivity between the application and Amazon S3 has been verified.
- The storage service is ready for the next AI document processing stages.

In the next section, we will continue with **5.3.3 – Verify and Manage Stored Documents in Amazon S3**.