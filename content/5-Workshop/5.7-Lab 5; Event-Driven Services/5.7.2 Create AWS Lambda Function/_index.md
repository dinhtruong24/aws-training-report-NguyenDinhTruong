---
title : "Create a Backup Plan"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.7.2. </b> "
---

In this section, we will create a **Backup Plan** to define how AWS Backup performs backup operations for the system's AWS resources.

A Backup Plan includes **Backup Rules**, backup schedules, retention periods, and the AWS resources assigned for backup. Configuring a Backup Plan automates the backup process and ensures that backups are created according to the defined protection policy.

---

## Step 1. Create a Backup Plan

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **AWS Backup** service.
2. Select **Backup plans**.
3. Click **Create Backup plan**.
4. Choose a backup plan creation method.
5. Enter the Backup Plan name.

Example:

```text
delivery-backup-plan
```

After completing the configuration, click **Create plan**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.2-create-backup-plan.png" width="900">
</p>

<p align="center">
<i>Figure 5.7.4. Creating a Backup Plan.</i>
</p>

---

## Step 2. Configure the Backup Rule

After creating the Backup Plan:

1. Click **Add backup rule**.
2. Enter the Backup Rule name.
3. Select the previously created Backup Vault.
4. Configure the backup schedule.
5. Specify the backup retention period.

After completing the configuration, click **Save**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.2-configure-backup-rule.png" width="900">
</p>

<p align="center">
<i>Figure 5.7.5. Configuring the Backup Rule.</i>
</p>

---

## Step 3. Assign Resources to the Backup Plan

After the Backup Plan has been created:

1. Click **Assign resources**.
2. Select the appropriate IAM role.
3. Choose the AWS resources to back up.
4. Save the configuration.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.2-assign-resources.png" width="900">
</p>

<p align="center">
<i>Figure 5.7.6. Assigning resources to the Backup Plan.</i>
</p>

---

## Configuration Summary

| Property | Value |
|---|---|
| AWS Service | AWS Backup |
| Resource | Backup Plan |
| Backup Rule | Daily Backup |
| Backup Vault | `delivery-backup-vault` |
| Status | Active |

---

## Result

After completing this section, you have successfully:

- Created a Backup Plan.
- Configured a Backup Rule.
- Defined the backup schedule and retention policy.
- Assigned AWS resources to the Backup Plan.
- Prepared the environment for running Backup Jobs.

In the next section, we will continue with **5.7.3 – Run and Verify Backup Jobs**.