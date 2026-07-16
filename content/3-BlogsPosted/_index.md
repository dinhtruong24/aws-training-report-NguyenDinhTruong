---
title: "Blogs Posted"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---
During **The First Cloud AI Journey** program, I researched, summarized, and shared technical articles from AWS Blogs to improve my knowledge of cloud computing, security, artificial intelligence, and system architecture on AWS.

The following articles focus on practical topics, including securing database credentials for AWS Lambda, proactively monitoring AWS infrastructure with AI agents, and connecting Amazon API Gateway to private resources within an Amazon VPC. Through researching and summarizing these articles, I strengthened my technical documentation reading, AWS architecture analysis, and knowledge-sharing skills.

###  [Blog 1 - Securing Database Credentials for AWS Lambda with AWS Secrets Manager](3.1-Blog1/)
This article explains how to securely manage database credentials for AWS Lambda by using AWS Secrets Manager instead of storing hardcoded passwords in source code.
- Architecture flow: API Gateway → Lambda → AWS Secrets Manager → Amazon RDS.
- Securely store credentials with AWS Secrets Manager.
- Enable automatic secret rotation. 
- Improve security for Serverless applications.

**Source:** [AWS Security Blog](https://aws.amazon.com/blogs/security/how-to-securely-provide-database-credentials-to-lambda-functions-by-using-aws-secrets-manager/)

###  [Blog 2 - AgentWatch: Proactive AWS Monitoring with Ambient Agents](3.2-Blog2/)
This article introduces AgentWatch, an AI-powered monitoring solution that proactively analyzes AWS infrastructure, detects issues, and assists DevOps teams in maintaining system reliability.
- Monitor CloudWatch Metrics, Logs, and Alarms.
- Analyze infrastructure data using Amazon Bedrock AgentCore.
- Send reports and alerts directly to Slack.
- Automate infrastructure monitoring with AI Agents.

**Source:** [AWS Machine Learning Blog](https://aws.amazon.com/blogs/machine-learning/agentwatch-proactive-aws-monitoring-with-ambient-agents/)

###  [Blog 3 - Understanding VPC Links in Amazon API Gateway Private Integrations](3.3-Blog3/)
This article explains how VPC Links enable Amazon API Gateway to securely connect with private resources inside an Amazon VPC without exposing backend services to the public internet.
- Learn the difference between Private APIs and Private Integrations.
- Understand AWS Hyperplane and AWS PrivateLink.
- Connect API Gateway with Network Load Balancers (NLB) or Application Load Balancers (ALB).
- Build secure, scalable, and highly available API architectures on AWS.

**Source:** [AWS Compute Blog](https://aws.amazon.com/blogs/compute/understanding-vpc-links-in-amazon-api-gateway-private-integrations/)