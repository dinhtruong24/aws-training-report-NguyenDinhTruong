---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 4 Objectives:

* Shift system design thinking from monolithic architecture to Microservices and Serverless architectures to improve scalability and flexibility.

* Understand DevOps principles by learning Continuous Integration and Continuous Delivery (CI/CD), infrastructure automation, and modern software delivery methodologies.

* Strengthen data security and privilege management by mastering encryption services, implementing strict permission boundaries, and exploring AI-powered threat detection solutions.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday | - Researched advanced access control using IAM Permission Boundaries; studied how Permission Boundaries limit the maximum permissions that can be granted to IAM Users and Roles, and configured policies to prevent privilege escalation by delegated administrators.  | 25/05/2026 | 25/05/2026      | https://000030.awsstudygroup.com/ |
| Tuesday  | - Deployed Amazon GuardDuty and performed security incident simulations; enabled Amazon GuardDuty, simulated attacks such as SSH brute-force attempts, malicious IP access, and port scanning, and analyzed the generated security findings.   | 26/05/2026 | 26/05/2026     | https://000098.awsstudygroup.com/ |
| Wednesday  | - Managed encryption keys with AWS KMS and secured data at rest; created Customer Managed Keys (CMK), configured key lifecycle management, defined key policies, and enabled automatic encryption for sensitive data stored in Amazon S3. | 27/05/2026 | 27/05/2026    | https://000033.awsstudygroup.com/ |
| Thursday  | - Studied the AWS Well-Architected Framework, focusing deeply on the Security Pillar; explored core principles including identity management, infrastructure protection, data protection, and incident response strategies.  | 28/05/2026 | 28/05/2026    | https://000097.awsstudygroup.com/ |
| Friday  | - Researched the fundamentals of Serverless architecture; learned how event-driven systems operate using AWS Lambda and Amazon API Gateway, and compared Serverless with traditional EC2-based architectures regarding cost optimization, auto-scaling, and cold start limitations.   | 29/05/2026 | 29/05/2026     | https://000054.awsstudygroup.com/ https://000078.awsstudygroup.com/ https://000079.awsstudygroup.com/ https://000082.awsstudygroup.com/ https://000084.awsstudygroup.com/ https://000085.awsstudygroup.com/ |


### Week 4 Achievements:

* Privilege Control & Threat Detection: Successfully established IAM Permission Boundaries to prevent privilege escalation and deployed Amazon GuardDuty to intelligently detect and flag simulated security threats.

* Optimal Data Protection: Mastered AWS KMS by provisioning and managing the lifecycle of Customer Managed Keys (CMKs), successfully enforcing automatic encryption on sensitive data resting in Amazon S3 buckets.

* Standardized Serverless Thinking: Acquired a solid understanding of event-driven system designs using AWS Lambda and API Gateway, while aligning security practices with the AWS Well-Architected Framework.

### Week 4 Evaluation:
* During the security incident simulation to test Amazon GuardDuty, I initially faced issues getting the external scanning tools to register because of pre-existing network security layers blocking the traffic. After setting up a temporary isolated sandbox VPC and adjusting the Security Groups, GuardDuty captured and analyzed the threats correctly. This provided me with a profound, hands-on understanding of how proactive security monitoring systems operate in real-world environments.
