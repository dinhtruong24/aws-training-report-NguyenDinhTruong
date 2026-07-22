---
title : "Create a CloudWatch Alarm"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.6.3. </b> "
---

In this section, we will create an **Amazon CloudWatch Alarm** to monitor the performance metrics of AWS resources.

A CloudWatch Alarm continuously monitors selected metrics and automatically changes its state when the metric value exceeds a predefined threshold. This allows administrators to detect issues quickly and respond before they affect the application.

---

## Step 1. Open CloudWatch Alarms

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon CloudWatch** service.
2. Select **Alarms**.
3. Click **Create alarm**.

---

## Step 2. Configure the Alarm

On the **Create alarm** page, perform the following steps:

1. Click **Select metric**.
2. Choose the metric to monitor.
3. Configure the alarm threshold.
4. Define the alarm condition.
5. Enter the alarm name.
6. Click **Create alarm**.

After the alarm has been created, CloudWatch will continuously monitor the selected metric.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.6-lab4/5.6.3-create-cloudwatch-alarm.png" width="900">
</p>

<p align="center">
<i>Figure 5.6.4. Creating an Amazon CloudWatch Alarm.</i>
</p>

---

## Step 3. Verify the Alarm

After the alarm has been created successfully:

- Open the **Alarms** list.
- Verify that the new alarm appears in the list.
- Check the current alarm status.
- Confirm that the alarm is monitoring the correct metric.

CloudWatch will continuously evaluate the selected metric and automatically update the alarm state whenever the configured condition changes.

---

## Configuration Summary

| Component | Description |
|---|---|
| AWS Service | Amazon CloudWatch |
| Resource | CloudWatch Alarm |
| Metric | Performance metric being monitored |
| Threshold | Alarm trigger threshold |
| Status | OK / Alarm / Insufficient Data |

---

## Result

After completing this section, you have successfully:

- Created a CloudWatch Alarm.
- Configured the performance metric to monitor.
- Defined the alarm threshold.
- Verified the alarm status.
- Completed **Lab 4 – CloudWatch Monitoring**.

After completing Lab 4, the system is capable of monitoring AWS resource performance and automatically generating alerts whenever configured thresholds are exceeded.