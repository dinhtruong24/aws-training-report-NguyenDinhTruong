---
title : "Lab 5: AWS Backup"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b>5.7. </b> "
---

In this lab, we will use **AWS Backup** to build a centralized backup solution for AWS resources.

AWS Backup is a fully managed backup service that enables you to create and manage **Backup Plans**, automate backup operations, and restore data whenever necessary. Using AWS Backup simplifies data protection while helping organizations meet security and compliance requirements.

In this lab, we will create a **Backup Vault**, configure a **Backup Plan**, assign AWS resources to the plan, and verify the backup results after the backup jobs have completed.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.1-open-aws-backup.png" width="900">
</p>

<p align="center">
<i>Figure 5.7.1. AWS Backup service dashboard.</i>
</p>

---

## Lab Objectives

After completing this lab, you will be able to:

- Access the AWS Backup service.
- Create a Backup Vault.
- Create a Backup Plan.
- Configure Backup Rules.
- Assign AWS resources to the Backup Plan.
- Run Backup Jobs.
- Verify backup status and results.
- Prepare the environment for future data recovery.

---

## Backup Architecture

In this lab, AWS Backup manages the backup process as follows:

```text
AWS Resources
       │
       ▼
AWS Backup
       │
       ├── Backup Vault
       ├── Backup Plan
       ├── Backup Rule
       └── Backup Jobs
```

AWS Backup automatically performs backup operations according to the schedule defined in the Backup Plan.

---

## Main Components

This lab uses the following AWS services and resources:

| Component | Description |
|---|---|
| AWS Backup | Centralized backup management service |
| Backup Vault | Stores backup recovery points |
| Backup Plan | Defines the backup strategy |
| Backup Rule | Specifies the backup schedule and retention settings |
| Backup Jobs | Tracks backup execution status |

---

## Lab Contents

Lab 5 consists of three sections:

### 5.7.1 Create a Backup Vault

In this section, we will:

- Access the AWS Backup service.
- Create a Backup Vault.
- Verify that the Backup Vault has been created successfully.

### 5.7.2 Create a Backup Plan

In this section, we will:

- Create a Backup Plan.
- Configure Backup Rules.
- Assign AWS resources to the Backup Plan.
- Verify the Backup Plan configuration.

### 5.7.3 Run and Verify Backup Jobs

In this section, we will:

- Start a Backup Job.
- Monitor the Backup Job status.
- Verify the backup results.
- Confirm that recovery points have been stored in the Backup Vault.

---

## Expected Results

After completing Lab 5:

- AWS Backup has been configured successfully.
- A Backup Vault has been created.
- A Backup Plan and Backup Rules have been configured.
- AWS resources have been assigned to the Backup Plan.
- Backup Jobs have completed successfully.
- Recovery points have been stored in the Backup Vault.
- The environment is ready for future data recovery operations.

After completing Lab 5, the system has a centralized and reliable backup solution implemented with AWS Backup.