---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---


# AGENTWATCH – PROACTIVE AWS INFRASTRUCTURE MONITORING USING AMBIENT AGENTS ON AMAZON BEDROCK

Modern cloud environments generate thousands of metrics, logs, and alarms every day. As infrastructure grows, operations teams often spend significant time monitoring dashboards, investigating alerts, and identifying the root causes of system issues. AgentWatch is an intelligent monitoring solution that combines Amazon Bedrock, AWS Lambda, Amazon CloudWatch, and Ambient Agents to automate infrastructure monitoring and provide proactive operational insights.

## Overview

AgentWatch continuously monitors AWS resources and automatically analyzes operational data using generative AI. Instead of waiting for engineers to investigate problems manually, the solution collects monitoring information, identifies abnormal behaviors, and delivers summarized reports to Slack.

## Solution Architecture

The architecture integrates several AWS services:

- Amazon EventBridge schedules monitoring tasks.
- AWS Lambda orchestrates the monitoring workflow.
- Amazon Cognito authenticates the requests.
- Amazon Bedrock AgentCore analyzes operational data.
- Amazon CloudWatch provides Metrics, Logs, and Alarms.
- Slack receives monitoring reports.

This architecture enables continuous monitoring without requiring engineers to manually inspect CloudWatch dashboards.

## Monitoring Workflow

The monitoring process consists of five main steps.

### Step 1 – Schedule Monitoring

Amazon EventBridge periodically triggers an AWS Lambda function to start the monitoring workflow.

### Step 2 – Collect Operational Data

Lambda retrieves CloudWatch Metrics, Logs, and Alarms from the monitored AWS environment.

### Step 3 – Analyze Data with Amazon Bedrock

The collected monitoring data is sent to Amazon Bedrock AgentCore, where an AI model analyzes infrastructure health, detects anomalies, and identifies potential root causes.

### Step 4 – Generate Reports

Lambda converts the AI analysis into a readable monitoring report containing:

- Infrastructure status
- Critical alarms
- Possible root causes
- Recommended actions

The report is automatically delivered to Slack.

### Step 5 – Human Approval

Before executing sensitive operations, AgentWatch requires human approval to ensure important infrastructure changes remain under administrator control.

## Benefits

AgentWatch provides several advantages:

- Automatically analyzes CloudWatch Metrics, Logs, and Alarms.
- Detects infrastructure anomalies proactively.
- Reduces manual monitoring effort.
- Improves incident response time.
- Integrates AI-powered operational analysis.
- Supports DevOps teams with intelligent recommendations.

## Conclusion

AgentWatch demonstrates how Amazon Bedrock can enhance AWS infrastructure monitoring by combining generative AI with existing monitoring services. The solution reduces operational workload, provides proactive insights, and improves the overall efficiency of cloud operations while maintaining human control over critical decisions.

<p align="center">
  <img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog2-agentwatch.png" width="700" alt="AgentWatch Architecture">
</p>

<p align="center">
<i>Figure 2. AgentWatch architecture for proactive AWS infrastructure monitoring using Amazon Bedrock.</i>
</p>

<p align="center">
<strong>Reference Article:</strong>
<a href="https://aws.amazon.com/blogs/machine-learning/agentwatch-proactive-aws-monitoring-with-ambient-agents/">
AWS Machine Learning Blog
</a>
</p>

<p align="center">
<strong>Community Post:</strong>
<a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2190168085081485">
AWS Study Group – Facebook
</a>
</p>