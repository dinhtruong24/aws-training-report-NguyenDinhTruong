---
title: "Week 12 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

* Strengthen IAM permission management by writing JSON-based IAM policies and applying advanced policy conditions.
* Create an AWS CLI cheat sheet to improve efficiency in daily cloud administration tasks.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday | - Optimized cloud object storage costs by implementing Amazon S3 Lifecycle rules and integrating S3 Glacier; created automated lifecycle transition criteria to dynamically transfer cold datasets into specialized Glacier storage tiers and set targeted expiration rules to eliminate long-term capacity costs.     | 20/07/2026 | 20/07/2026      | https://000078.awsstudygroup.com/ |
| Tuesday  | - Maintained advanced configurations for Amazon S3 Lifecycle and S3 Glacier workflows; performed detailed audits of multi-tier lifecycle transitions, evaluated cost-effective storage classes, and tested object expiration policies to perfect cost optimization models.   | 21/07/2026 | 21/07/2026      | https://000069.awsstudygroup.com/ https://000111.awsstudygroup.com/ |
| Wednesday | - Compiled a comprehensive AWS CLI command cheat sheet cataloging essential management syntax for Amazon EC2, Amazon S3, IAM, Amazon RDS, and Amazon CloudWatch; specialized in programmatic command manipulation utilizing --query projections, structural --filter arguments, and versatile output renders including JSON text and clean tabular charts. | 22/07/2026 | 22/07/2026     | https://000011.awsstudygroup.com/ |
| Thursday  | - Researched the fundamental principles of the Security Pillar embedded inside the AWS Well-Architected Framework; investigated standardized workflows regarding modern identity infrastructure, data protection boundaries, and tactical incident response blueprints.     | 23/07/2026 | 23/07/2026      | https://000141.awsstudygroup.com/ |
| Friday | - Explored the structural best practices within the Operational Excellence Pillar of the AWS Well-Architected Framework; focused on running operational automations, monitoring infrastructure runtime status, and sustaining continuous evolutionary improvement workflows.     | 24/07/2026 | 24/07/2026      | https://000098.awsstudygroup.com/ |


### Week 12 Achievements:

* Automated Data Lifecycle Sorting: Successfully deployed S3 Lifecycle configurations to dynamically offload stale objects into S3 Glacier vaults, realizing significant database and object storage financial savings.

* Command Line Administration Mastery: Generated a fully-functional AWS CLI Cheat Sheet and gained high proficiency in sorting large cloud infrastructure metadata using advanced filtering structures like --query and --filter.

* Standardized Cloud Governance Mindset: Acquired professional-grade familiarity with both the Security and Operational Excellence Pillars outlined in the AWS Well-Architected Framework, providing a sturdy checklist for testing production system reliability.

### Week 12 Evaluation:
* On Wednesday, while drafting the AWS CLI Cheat Sheet and parsing a massive payload of structural metadata from a high volume of Amazon EC2 targets, the default API outputs executed slowly and flooded the terminal window with unreadable, messy raw JSON blocks. This provided an excellent hands-on lesson regarding command-line operations overhead. I successfully resolved the visual clutter and latency bottleneck by chaining structural --query syntax to only target critical infrastructure attributes (such as InstanceId and current State) and formatting the console presentation layer with --output table parameters, making everyday system diagnostics instantly scannable and highly readable.