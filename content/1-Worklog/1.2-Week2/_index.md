---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Install, configure, and master AWS resource management utilizing the Command Line Interface (AWS CLI).
* Research, initialize, and practice establishing database connections and queries on both relational (Amazon RDS) and non-relational (Amazon DynamoDB) systems.
* Explore rapid application deployment with Amazon Lightsail and design a highly available, auto-scaling, and load-balanced infrastructure (Auto Scaling & ELB) on Amazon EC2.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday   | - Installed and configured the AWS CLI on a personal computer using Access Keys/Secret Access Keys, and practiced basic CLI commands to manage EC2, S3, and Key Pair resources. | 11/05/2026 | 11/05/2026      | https://000011.awsstudygroup.com/ |
| Tuesday  | - Researched the Amazon RDS (MySQL) managed database service, configured Security Groups, Endpoints, and successfully connected via a client tool to perform database queries. | 12/05/2026 | 12/05/2026      | https://000005.awsstudygroup.com/ |
| Wednesday   | - Explored the Amazon DynamoDB NoSQL database model, designed table schemas utilizing Partition Keys and Sort Keys, and successfully executed basic CRUD operations. | 13/05/2026 | 13/05/2026      | https://000060.awsstudygroup.com/ https://000039.awsstudygroup.com/ https://0000133.awsstudygroup.com/ |
| Thursday   | - Discovered Amazon Lightsail, deployed a WordPress instance quickly, configured basic DNS settings, and compared Lightsail with Amazon EC2 for lightweight applications.  | 14/05/2026 | 14/05/2026      | https://000045.awsstudygroup.com/ https://000046.awsstudygroup.com/ |
| Friday   | - Researched high scalability and availability architectures by creating a Launch Template, configuring an Auto Scaling Group (with CPU-based Scale-In/Scale-Out policies), and integrating it with an Elastic Load Balancer (ELB).  | 15/05/2026 | 15/05/2026      | https://000006.awsstudygroup.com/ |


### Week 2 Achievements:

* Flexible System Administration: Successfully configured the AWS CLI on a local machine and efficiently managed AWS resources through command-line inputs instead of the web Console.

* Dual Database Architecture Mastery: Deployed and connected to both relational Amazon RDS (MySQL) and non-relational Amazon DynamoDB databases, performing seamless query connections and CRUD operations.

* Highly Scalable Infrastructure Deployment: Deployed a fully functional WordPress website on Amazon Lightsail and successfully built an Auto Scaling Group combined with a Load Balancer, validating automatic scaling behaviors under simulated workloads.web interface.

### Week 2 Evaluation:
* During the hands-on configuration of the Auto Scaling Group combined with the Elastic Load Balancer, I initially faced difficulties setting up appropriate threshold policies for CPU-based Scale-Out and Scale-In, which caused sub-optimal scaling responses during the first trial. After adjusting the cooldown periods and refining the CPU metric thresholds, the system successfully provisioned and terminated instances in exact accordance with the real workload demands.
