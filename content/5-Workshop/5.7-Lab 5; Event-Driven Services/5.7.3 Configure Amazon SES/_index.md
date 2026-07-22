---
title : "Run and Verify Backup Jobs"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.7.3. </b> "
---

In this section, we will run a **Backup Job** and verify the backup results using AWS Backup.

A Backup Job is the process in which AWS Backup creates backup copies of the AWS resources assigned to a Backup Plan. After the job is completed, the backups are stored as **Recovery Points** in the Backup Vault and are available for future data recovery.

---

## Step 1. Run a Backup Job

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **AWS Backup** service.
2. Select **Protected resources** or **Backup plans**.
3. Choose the resource to back up.
4. Click **Create on-demand backup** or start the backup according to the configured Backup Plan.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.3-start-backup-job.png" width="900">
</p>

<p align="center">
<i>Figure 5.7.7. Running a Backup Job.</i>
</p>

---

## Step 2. Review Backup Jobs

After the Backup Job has been created:

1. Select **Backup jobs**.
2. Check the status of the Backup Job.
3. Confirm that the backup process has completed successfully.

The Backup Job status may be one of the following:

- Running
- Completed
- Failed

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.3-view-backup-jobs.png" width="900">
</p>

<p align="center">
<i>Figure 5.7.8. Reviewing Backup Jobs.</i>
</p>

---

## Step 3. Verify the Backup Results

After the Backup Job has completed successfully:

- Open the **Backup Vault**.
- Verify that the **Recovery Points** have been created.
- Confirm that the backup data has been stored successfully.
- Review the creation time and status of the recovery points.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.3-verify-backup-results.png" width="900">
</p>

<p align="center">
<i>Figure 5.7.9. Verifying the backup results.</i>
</p>

---

## Configuration Summary

| Property | Description |
|---|---|
| AWS Service | AWS Backup |
| Backup Job | Backup operation |
| Backup Vault | Storage location for Recovery Points |
| Recovery Point | Backup copy of an AWS resource |
| Status | Running / Completed / Failed |

---

## Result

After completing this section, you have successfully:

- Run a Backup Job.
- Monitored the Backup Job status.
- Verified the Recovery Points stored in the Backup Vault.
- Confirmed that the backup data has been stored successfully.
- Completed **Lab 5 – AWS Backup**.

After completing Lab 5, the system has a centralized backup solution and is ready to restore data whenever necessary.