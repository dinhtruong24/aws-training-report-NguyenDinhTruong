---
title : "View CloudWatch Metrics"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.6.2. </b> "
---

In this section, we will use **Amazon CloudWatch Metrics** to monitor the performance of AWS resources.

Amazon CloudWatch automatically collects performance metrics from AWS services such as Amazon EC2, Amazon RDS, and the Application Load Balancer. These metrics help evaluate system health and detect potential performance issues at an early stage.

---

## Step 1. Open CloudWatch Metrics

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Open the **Amazon CloudWatch** service.
2. Select **Metrics**.
3. Choose the AWS service that you want to monitor.

---

## Step 2. View Performance Metrics

On the **Metrics** page, you can monitor performance indicators such as:

- CPU Utilization
- Network In
- Network Out
- Disk Read Operations
- Disk Write Operations

The charts display performance data over time, allowing you to evaluate the operational status of AWS resources.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.6-lab4/5.6.2-view-cloudwatch-metrics.png" width="900">
</p>

<p align="center">
<i>Figure 5.6.3. Viewing Amazon CloudWatch Metrics.</i>
</p>

---

## Step 3. Verify the Metrics

After opening the Metrics page:

- Verify that the performance charts are displayed correctly.
- Review CPU utilization.
- Monitor Network In and Network Out traffic.
- Observe performance trends over time.

This information will be used to evaluate system performance and prepare the configuration of CloudWatch Alarms in the next section.

---

## Metrics Summary

| Metric | Description |
|---|---|
| CPU Utilization | Percentage of CPU usage |
| Network In | Incoming network traffic |
| Network Out | Outgoing network traffic |
| Disk Read Operations | Number of disk read operations |
| Disk Write Operations | Number of disk write operations |

---

## Result

After completing this section, you have successfully:

- Accessed Amazon CloudWatch Metrics.
- Monitored the performance of AWS resources.
- Reviewed CPU utilization and network traffic metrics.
- Collected the information required to configure CloudWatch Alarms.

In the next section, we will continue with **5.6.3 – Create a CloudWatch Alarm**.