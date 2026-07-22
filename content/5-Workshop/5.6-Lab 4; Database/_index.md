---
title : "Lab 4: CloudWatch Monitoring"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b>5.6. </b> "
---

In this lab, we will use **Amazon CloudWatch** to monitor the AWS resources deployed in the system.

Amazon CloudWatch is AWS's monitoring and observability service that collects **Metrics**, **Logs**, and **Events** from AWS services such as Amazon EC2, Amazon RDS, and the Application Load Balancer.

In addition to monitoring system performance, CloudWatch allows you to create alarms that automatically notify administrators whenever a resource exceeds a predefined threshold.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.6-lab4/5.6.1-open-cloudwatch-dashboard.png" width="900">
</p>

<p align="center">
<i>Figure 5.6.1. Amazon CloudWatch Dashboard.</i>
</p>

---

## Lab Objectives

After completing this lab, you will be able to:

- Access the Amazon CloudWatch Dashboard.
- Monitor system metrics.
- Review the performance of EC2 instances.
- Monitor CPU, Network, and other AWS resource metrics.
- Create CloudWatch Alarms.
- Configure alarm conditions.
- Prepare a monitoring environment for the application.

---

## Monitoring Architecture

In this lab, Amazon CloudWatch collects metrics from AWS resources as illustrated below:

```text
EC2 Instance
        │
        ▼
Amazon CloudWatch
        │
        ├── Metrics
        ├── Dashboard
        └── Alarm
```

CloudWatch continuously collects performance data to help monitor system health and generate alerts when necessary.

---

## Main Components

This lab uses the following AWS services and resources:

| Component | Description |
|---|---|
| Amazon CloudWatch | AWS monitoring and observability service |
| Dashboard | Displays monitoring information |
| Metrics | Performance data collected from AWS resources |
| Alarm | Sends notifications when a metric exceeds a configured threshold |

---

## Lab Contents

Lab 4 consists of three sections:

### 5.6.1 Open the CloudWatch Dashboard

In this section, we will:

- Open the Amazon CloudWatch service.
- Access the CloudWatch Dashboard.
- Explore the monitoring interface.

### 5.6.2 View CloudWatch Metrics

In this section, we will:

- View EC2 metrics.
- Monitor CPU Utilization.
- Monitor Network In and Network Out.
- Review the operational status of AWS resources.

### 5.6.3 Create a CloudWatch Alarm

In this section, we will:

- Create a new CloudWatch Alarm.
- Select the metric to monitor.
- Configure the alarm threshold.
- Verify the alarm after it has been created.

---

## Expected Results

After completing Lab 4:

- Amazon CloudWatch has been configured successfully.
- The dashboard displays the system metrics.
- EC2 instance performance can be monitored.
- A CloudWatch Alarm has been created successfully.
- The system is capable of monitoring AWS resources and generating alerts when required.

After completing Lab 4, the environment will be ready for **Lab 5 – AWS Backup**.