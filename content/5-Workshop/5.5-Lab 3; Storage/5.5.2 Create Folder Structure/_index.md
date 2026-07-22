---
title : "Create the Folder Structure"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.5.2. </b> "
---

In this section, we will create the folder structure inside the Amazon S3 Bucket to organize the application's data.

Organizing files into separate folders makes it easier to manage documents, uploaded files, and backup data. A well-structured storage layout also improves maintainability and simplifies future application development.

---

## Step 1. Open the Amazon S3 Bucket

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon S3** service.
2. Select **Buckets**.
3. Open the following bucket:

```text
delivery-dev-storage
```

The bucket is initially empty and ready for creating folders.

---

## Step 2. Create the Folder Structure

Inside the bucket, click **Create folder**.

Create the following folders:

```text
documents/
```

```text
uploads/
```

```text
backups/
```

Each folder serves a different purpose:

| Folder | Description |
|---|---|
| `documents/` | Stores application documents |
| `uploads/` | Stores files uploaded by users |
| `backups/` | Stores backup files |

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.5-lab3/5.5.2-create-folder-structure.png" width="900">
</p>

<p align="center">
<i>Figure 5.5.3. Creating the folder structure inside the Amazon S3 Bucket.</i>
</p>

---

## Step 3. Verify the Folder Structure

After creating all folders successfully:

- Open the Amazon S3 Bucket.
- Verify that all folders are displayed.
- Confirm that each folder has been created correctly.

The bucket structure should appear as follows:

```text
delivery-dev-storage
│
├── documents/
├── uploads/
└── backups/
```

This folder structure will be used by the application to organize different types of data.

---

## Folder Structure Summary

| Folder | Purpose |
|---|---|
| `documents/` | Stores application documents |
| `uploads/` | Stores user-uploaded files |
| `backups/` | Stores backup data |

---

## Result

After completing this section, you have successfully:

- Created the folder structure inside the Amazon S3 Bucket.
- Organized application data into separate directories.
- Improved storage management for future development.
- Prepared the Amazon S3 Bucket for storing application data.

In the next section, we will continue with **5.5.3 – Configure the S3 Gateway Endpoint**.