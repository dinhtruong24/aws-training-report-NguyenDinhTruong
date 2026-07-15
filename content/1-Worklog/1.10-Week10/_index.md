---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 10 Objectives:

* Outline the system architecture for the final personal project by defining the comprehensive solution blueprint and identifying ideal AI/ML integrations to tackle a real-world scenario.
* Study corporate-level resource isolation through the Enterprise Multi-Account Strategy, understanding how to containerize organizational blast radiuses in high-scale cloud designs.
* Implement centralized governance and cloud security controls by orchestrating granular permission sets, centralized consolidated billing, and federated cross-account access patterns.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Drafted the technical infrastructure diagrams and mapped out the machine learning capability integration roadmap for the final personal capstone project.     | 06/07/2026 | 06/07/2026      | https://cloudjourney.awsstudygroup.com/ |
| Tuesday | - Investigated multi-account enterprise paradigms; analyzed security vulnerabilities and administrative concerns of executing workloads within a singular AWS account (such as catastrophic blast radius expansion, billing visualization issues, and developer resource overrides), and studied the structural concepts of AWS Landing Zones.    | 07/07/2026 | 07/07/2026      | https://000002.awsstudygroup.com/ https://000030.awsstudygroup.com/ https://000031.awsstudygroup.com/ |
| Wednesday  | - Built a secure AWS Organizations hierarchy; initiated the organization structure from the primary Management Account, successfully associated designated member accounts, and enabled Consolidated Billing features to enforce centralized billing operations. | 08/07/2026 | 08/07/2026      | https://000027.awsstudygroup.com/ |
| Thursday  | - Structured logical Organizational Units (OUs) and enforced strict Service Control Policies (SCPs); grouped member accounts into isolated Dev, Test, Production, and Security environments, and drafted SCP boundaries to restrict deployment of expensive service classes and block unapproved AWS Regions.   | 09/07/2026 | 09/07/2026      | https://000064.awsstudygroup.com/ https://000010.awsstudygroup.com/ |
| Friday  | - Configured enterprise access control using AWS IAM Identity Center; modeled secure Permission Sets and deployed Federated Cross-Account Access to allow staff to sign into multiple target environments safely via a single portal.      | 10/07/2026 | 10/07/2026      | https://000096.awsstudygroup.com/ |
| Saturday  | - Finalized the technical write-up for Blog 3, and engineered the serverless container computing layer using Amazon ECS Fargate for the final personal project.    | 11/07/2026  | 11/07/2026       | https://cloudjourney.awsstudygroup.com/ |


### Week 10 Achievements:

* Project Blueprinting & Container Provisioning: Successfully designed the target system architecture with integrated AI services, authored Technical Blog 3, and deployed live containerized components on AWS ECS Fargate.

* Enterprise-grade Multi-Account Foundation: Constructed an AWS Organizations topology linking separate member accounts to a centralized root account, consolidating financial billing and usage data reporting.

* Unified Directory Access & Tenant Security: Built structured OUs (separating Dev, Test, Prod, and Security), enforced global restrictions on costly components using JSON SCPs, and centralized developer single sign-on (SSO) credentials using AWS IAM Identity Center.

### Week 10 Evaluation:
* On Thursday, right after locking down the Dev Organizational Unit (OU) via strict Service Control Policies (SCPs) to prohibit expensive instance types, certain essential shared pipeline resources crashed with Access Denied errors during deployment. This was an impactful real-world lesson on how SCPs act as a master filter that overrides any standard IAM policies. I resolved the issue by auditing AWS CloudTrail logs, narrowing down the denied API actions, and updating the JSON SCP conditions to isolate high-cost instances while preserving standard operational pipelines for developers.