---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 7 Objectives:

* Run and optimize a production-ready CI/CD loop by automating the end-to-end code delivery pipeline from GitHub repositories down to Amazon ECS.
* Elevate database tier resilience and horizontal scalability by configuring robust disaster recovery blueprints for Amazon RDS and cutting down operational overhead for Amazon DynamoDB.
* Explore big data processing capabilities by studying real-time ingestion, transport, and analysis of live streaming data workloads via AWS services.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Built a fully automated, end-to-end CI/CD delivery chain; configured GitHub Webhooks to trigger automated AWS CodeBuild workflows that package software into Docker images, push them to Amazon ECR, and coordinate rolling ECS task upgrades via AWS CodeDeploy.      | 15/06/2026 | 15/06/2026      | https://000051.awsstudygroup.com/ https://000099.awsstudygroup.com/ https://000152.awsstudygroup.com/ |
| Tuesday  | - Executed deployment stress tests and monitored pipeline behaviors; pushed code changes to GitHub to evaluate automatic triggers, monitored the Rolling Update process to verify zero-downtime deployment, and parsed build runtimes to eliminate pipeline bottlenecks.         | 16/06/2026 | 16/06/2026      | 	https://000062.awsstudygroup.com/ https://000084.awsstudygroup.com/ https://000113.awsstudygroup.com/ |
| Wednesday  | - Hardened the reliability and read performance of Amazon RDS; set up a Multi-AZ deployment blueprint to ensure automated database failover capability, and provisioned Read Replicas to offload high-read query workloads from the master node. | 17/06/2026 | 17/06/2026      |  https://100000.awsstudygroup.com/ https://100001.awsstudygroup.com/ |
| Thursday  | - Optimized the operational throughput of Amazon DynamoDB; researched Global Secondary Indexes (GSI) designs, configured highly-dispersed partition keys to mitigate hot partition issues, and reduced RCU/WCU consumption rates to optimize costs.                       | 18/06/2026 | 18/06/2026      | https://000039.awsstudygroup.com/ https://000078.awsstudygroup.com/ |
| Friday  | - Explored cloud-native real-time data streaming using Amazon Kinesis; analyzed the differences between Kinesis Data Streams and Kinesis Data Firehose, configured real-time log ingestion mechanisms, and channeled active telemetry streams directly into Amazon S3 and Amazon OpenSearch destinations.        | 19/06/2026 | 19/06/2026     | https://000035.awsstudygroup.com/ https://000070.awsstudygroup.com/ https://000072.awsstudygroup.com/ https://000105.awsstudygroup.com/ |


### Week 7 Achievements:

* E2E Delivery Pipeline Automation: Successfully constructed a highly efficient GitHub-triggered CI/CD pipeline, completely automating the application build, ECR registry storage, and zero-downtime rolling deployments on Amazon ECS.

* Enhanced Database Architecture Resilience: Strengthened relational database high availability with RDS Multi-AZ configurations, optimized read response times with dedicated Read Replicas, and successfully reduced NoSQL operational expenses via GSI optimizations.

* Real-time Data Ingestion Foundations: Gained functional knowledge on implementing event-driven data streaming pipelines with Amazon Kinesis, successfully managing real-time data delivery to reliable storage targets.

### Week 7 Evaluation:
* During the pipeline monitoring on Tuesday, rapid test deployments occasionally triggered resource allocation failures in the ECS cluster because older tasks were not draining fast enough while new containers were being provisioned. This offered a great real-world lesson on service deployment configurations. I successfully resolved the issue by adjusting the minimum healthy percentage and maximum execution limits (minimumHealthyPercent and maximumPercent) in the ECS service settings, ensuring a flawless rolling transition without compromising service availability.