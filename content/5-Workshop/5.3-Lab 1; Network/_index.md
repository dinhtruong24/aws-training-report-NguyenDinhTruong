---
title : "Lab 1: Document Storage & Upload"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

Welcome to **Lab 1** of this workshop. In this lab, we will build the document storage foundation for the **VietAI Scholar Assistant** system by deploying AWS storage services. This is the first and most important step that enables the AI components to access and process documents in the following labs.

All academic documents will be uploaded by users through the application. After being stored in Amazon S3, the documents will be ready for OCR, content analysis, summarization, translation, and AI-powered question answering.

## Lab 1 Architecture

In this lab, we will focus on the following components:

1. **Amazon S3:** Create a bucket to store PDF documents and input data.
2. **Document Upload:** Configure the document upload process from the application to Amazon S3.
3. **Storage Verification:** Verify that the uploaded documents are stored correctly on AWS.

## Step-by-Step Instructions

Lab 1 is divided into the following steps. Please complete them in order:

- **5.3.1 Create Amazon S3 Bucket:** Create a bucket for storing documents.
- **5.3.2 Configure Document Upload:** Configure the document upload process to Amazon S3.
- **5.3.3 Store Documents:** Verify and manage the stored documents.
- **5.3.4 Test Upload Workflow:** Test the complete document upload workflow.

---

Are you ready?

Let's begin with the first step: **Create Amazon S3 Bucket**.