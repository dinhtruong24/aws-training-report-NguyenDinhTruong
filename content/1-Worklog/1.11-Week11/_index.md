---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 11 Objectives:

* Reinforce cloud network perimeters by auditing the Amazon VPC topology and engineering a multi-layered firewall defense framework to safeguard enterprise infrastructure.
* Optimize cloud financial management and dynamic architecture scaling by exploring multi-account budget allocation methods and building advanced Auto Scaling triggers driven by live runtime metrics.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Implemented secure cross-environment delegation profiles using AWS STS Assume Role configurations; leveraged AWS Security Token Service (STS) to grant IAM Users and Roles inside the Management Account short-lived, encrypted credentials to perform operations in Development and Production accounts without exposing long-term access keys.      | 13/07/2026 | 13/07/2026      | https://000018.awsstudygroup.com/ |
| Tuesday  | - Extended programmatic testing for cross-environment trust relationships with AWS STS Assume Role pipelines; consolidated identity control models and refined centralized access policies across the multi-account AWS organization.      | 14/07/2026 | 14/07/2026      | https://000097.awsstudygroup.com/ |
| Wednesday  | - Optimized cost breakdown metrics within a multi-tenant cloud organization; evaluated the structural advantages of Consolidated Billing features inside AWS Organizations and integrated AWS Cost Explorer alongside custom Cost Allocation Tags to map cloud expenditure directly to internal teams and project initiatives. | 15/07/2026 | 15/07/2026      | https://000075.awsstudygroup.com/ |
| Thursday  | - Conducted a comprehensive structural review of Amazon VPC networking layouts and advanced firewall settings; audited Subnet distribution paths, Route Tables logic, Internet Gateways, and NAT Gateways, while configuring strict Security Groups and Network ACLs (NACLs) to establish a multi-layered security boundary.      | 16/07/2026 | 16/07/2026     | https://000019.awsstudygroup.com/ https://000074.awsstudygroup.com/ https://000111.awsstudygroup.com/ |
| Friday  | - Engineered an advanced Auto Scaling framework triggered by dynamic Memory Utilization; integrated an Application Load Balancer (ALB) deployment backed by an Auto Scaling Group (ASG), and established a custom Amazon CloudWatch metric pipeline to scale EC2 fleet capacities based on RAM consumption instead of standard CPU thresholds.      | 17/07/2026 | 17/07/2026      | https://000061.awsstudygroup.com/ https://000006.awsstudygroup.com/ |


### Week 11 Achievements:

* Hardened Cross-Account Trust Federation: Successfully deployed production-grade Cross-Account access infrastructure via AWS STS Assume Role, entirely mitigating identity exposure risks by replacing persistent access keys with ephemeral security tokens.

* Granular Financial Cost Tracking: Mastered the utilization of AWS Cost Explorer integrated with Cost Allocation Tags, delivering transparent financial cost reporting across isolated environments in a multi-tenant topology.

* Resilient Networking & Intelligent Architecture Scaling: Solidified VPC traffic patterns through synchronized Security Groups and stateless NACL logic, while successfully deploying a CloudWatch Custom Metric workflow to scale the ASG cluster efficiently based on real-time RAM usage.

### Week 11 Evaluation:
* On Friday, when deploying the custom CloudWatch metric to track RAM usage for dynamic Auto Scaling triggers, the ASG failed to scale out because the custom metric stream appeared blank in the console. This provided an essential architectural lesson on cloud monitoring boundaries: standard AWS virtualization metrics do not possess visibility into internal OS-level metrics like RAM. I successfully mitigated the issue by installing and configuring the Unified CloudWatch Agent daemon directly within the EC2 instances' operating systems, authorizing it to stream Memory Utilization metrics to CloudWatch consistently and enabling a fully responsive Auto Scaling cycle.
