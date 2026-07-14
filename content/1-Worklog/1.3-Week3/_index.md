---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 3 Objectives:

* Strengthen end-to-end system security by implementing security solutions across multiple layers, from identity and access management to application-layer protection.
* Improve risk management and proactive threat detection by configuring firewalls, evaluating security compliance, and establishing automated rules to detect and prevent unauthorized access.
* Secure sensitive data through encryption and optimize application deployment by standardizing large-scale containerized workloads.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Deployed a large-scale container architecture using Amazon ECS; created and configured an Amazon ECS Cluster, defined standardized Task Definitions, and deployed an Amazon ECS Service integrated with an Application Load Balancer (ALB) to ensure high availability.  | 18/05/2026 | 18/05/2026     | https://000016.awsstudygroup.com/ https://0000118.awsstudygroup.com/ |
| Tuesday  | - Integrated centralized monitoring with Amazon CloudWatch; configured metrics and log collection from Amazon ECS, built CloudWatch Dashboards to visualize system performance, and configured CloudWatch Alarms to send notifications through Email or Slack when CPU or memory usage exceeds the defined threshold.  | 19/05/2026 | 19/05/2026      | https://000008.awsstudygroup.com/ |
| Wednesday  | - Standardized identity management with AWS IAM Identity Center (SSO); configured centralized AWS Single Sign-On, created Permission Sets, and managed user access across Development, Staging, and Production environments.. | 20/05/2026 | 20/05/2026      | https://000028.awsstudygroup.com/ https://000031.awsstudygroup.com/ https://000044.awsstudygroup.com/ https://000058.awsstudygroup.com/ |
| Thursday | - Enabled AWS Security Hub and performed security compliance assessments; configured AWS Security Hub, ran automated security scans, and evaluated compliance based on the CIS AWS Foundations Benchmark to identify security misconfigurations. | 21/05/2026 | 21/05/2026     | https://000018.awsstudygroup.com/ https://000069.awsstudygroup.com/ |
| Friday  | - Configured AWS WAF to protect web applications; associated AWS WAF with an Application Load Balancer, created Web ACLs, and configured security rules to detect and block common attacks such as SQL Injection (SQLi), Cross-Site Scripting (XSS), and malicious bot traffic.  | 22/05/2026 | 22/05/2026      | https://000026.awsstudygroup.com/ |


### Week 3 Achievements:

* Standardized Container Operations: Successfully deployed containerized workloads on Amazon ECS integrated with an Application Load Balancer (ALB), optimizing routing, traffic distribution, and service fault tolerance.

* Comprehensive Automated Monitoring: Established a centralized visualization dashboard and configured automated alarms using Amazon CloudWatch to proactively track the metrics and operational health of ECS tasks.

* Multi-Layered Security Baseline: Completed centralized user access governance with AWS IAM Identity Center (SSO), achieved compliance standardizations with AWS Security Hub (CIS Benchmarks), and built a robust firewall defense using AWS WAF.

### Week 3 Evaluation:

* During the hands-on configuration of associating AWS WAF with the Application Load Balancer, I initially faced some issues with over-restrictive SQL Injection and bot-blocking rules, which accidentally blocked several legitimate API requests from client applications (false positives). After analyzing access logs via CloudWatch Logs and refining the rule exclusion patterns within the Web ACL, the firewall operated smoothly, ensuring security without disrupting the application's regular user traffic.