---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Master Cloud-Native and Serverless technologies by building and configuring serverless applications, reducing infrastructure management overhead, and optimizing operational costs.
* Learn modern system architecture by studying application decomposition and transitioning from Monolithic architecture to flexible Microservices architecture.
* Develop a DevOps mindset by understanding the fundamentals of Continuous Integration and Continuous Deployment (CI/CD), laying the foundation for automating the software delivery pipeline from development to production.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Built backend logic using AWS Lambda; developed, optimized, and configured AWS Lambda functions for backend data processing, practiced configuring IAM Roles, Memory allocation, Timeout settings, and securely managed Environment Variables.  | 01/06/2026 | 01/06/2026      | https://0000130.awsstudygroup.com/ https://000022.awsstudygroup.com/ |
| Tuesday  | - Integrated Amazon API Gateway and completed the Serverless workflow; deployed Amazon API Gateway (HTTP/REST API) as the request entry point, configured routing, and integrated it directly with AWS Lambda to build a secure, end-to-end serverless application   | 02/06/2026 | 02/06/2026      | https://000135.awsstudygroup.com/ |
| Wednesday  | - Studied Microservices architecture; learned how to decompose a Monolithic application into independent Microservices based on Bounded Context principles, and analyzed communication patterns using synchronous protocols (REST and gRPC) and asynchronous messaging through Event Brokers. | 03/06/2026 | 03/06/2026      | https://000050.awsstudygroup.com/ https://000052.awsstudygroup.com/ |
| Thursday  | - Studied CI/CD pipeline fundamentals; learned the concepts of Continuous Integration (CI) and Continuous Deployment (CD), analyzed the standard pipeline stages (Source $\rightarrow$ Build $\rightarrow$ Test $\rightarrow$ Deploy) and deployment strategies such as Blue-Green Deployment and Canary Deployment.  | 04/06/2026 | 04/06/2026      | https://000017.awsstudygroup.com/ https://000051.awsstudygroup.com/ https://000084.awsstudygroup.com/ https://000133.awsstudygroup.com/ |
| Friday | - Optimized the Serverless lab and evaluated real-world performance; completed the sample Serverless application, performed load testing, evaluated Lambda latency, Cold Start behavior, and automatic scaling under increasing workloads.  | 05/06/2026 | 05/06/2026      | https://000078.awsstudygroup.com/ |


### Week 5 Achievements:

* End-to-End Serverless Construction: Successfully developed a functional serverless backend by seamlessly integrating Amazon API Gateway with AWS Lambda functions optimized for memory, security, and execution timeouts.

* Modern Architectural Understanding: Mastered the principles of decomposing Monolithic systems into Microservices utilizing Bounded Context concepts, distinguishing clearly between synchronous (REST/gRPC) and asynchronous communication methods via Event Brokers.

* DevOps & CI/CD Foundations: Acquired thorough knowledge of the standard stages of a CI/CD pipeline and risk-mitigating deployment strategies (Canary, Blue-Green), and successfully optimized Serverless application performance by analyzing and managing Cold Start behaviors.

### Week 5 Evaluation:
* During the load testing of the Serverless application on Friday, I observed a significant latency spike caused by the initial Cold Start behavior of newly provisioned AWS Lambda instances. To optimize system performance, I researched and applied Provisioned Concurrency to the critical, latency-sensitive execution paths. This hands-on challenge provided me with a profound understanding of balancing operational costs against performance constraints in a Serverless environment.