---
title : "Workshop Overview"
date : 2024-01-01 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

## Introduction

In this workshop, we will deploy **VietAI Scholar Assistant** – an academic research support system built on the AWS Cloud platform and integrated with Artificial Intelligence (AI) technologies. The objective of the project is to build a platform capable of automatically analyzing academic documents, supporting translation, summarizing content, answering context-based questions, and helping learners access documents more quickly and effectively.

The system is designed to receive one or multiple PDF documents from users. After the documents are uploaded, the system automatically performs the analysis, processing, and data storage workflow. The final results include document summaries, translated content, question-answering capabilities based on the document content, and other learning support information.

The entire processing workflow is deployed on AWS using a serverless architecture to reduce operational costs, improve scalability, and simplify infrastructure management.

---

## Workshop Objectives

After completing this workshop, participants will be able to:

- Understand the process of building an AI-powered academic document processing system on AWS.
- Deploy a document storage system using Amazon S3.
- Build a document processing workflow using AWS Lambda and Amazon Bedrock.
- Understand how a Multi-Agent model works in document processing.
- Build a Retrieval-Augmented Generation (RAG) system for contextual search and question answering.
- Manage data and processing status using Amazon DynamoDB.
- Apply AWS security services to protect resources and user data.

---

## System Architecture

The project uses a serverless architecture combined with AWS AI services to build a complete academic document processing system.

Users access the web application to upload PDF documents. After a document is stored in Amazon S3, the upload event triggers AWS Lambda to execute the processing workflow.

AWS Lambda acts as the orchestrator and sends requests to Amazon Bedrock to analyze the document content. During this process, the system uses multiple AI Agents to perform different tasks, including content analysis, translation, document summarization, and context-based question answering.

After the processing is completed, the results are stored back in Amazon S3. At the same time, the processing status and document information are stored in Amazon DynamoDB for retrieval and management.

---

## AWS Services Used

The workshop uses the following AWS services:

- Amazon S3
- Amazon API Gateway
- AWS Lambda
- Amazon Bedrock
- Amazon DynamoDB
- Amazon Cognito
- AWS IAM
- Amazon CloudFront
- AWS KMS

Each service performs a specific role in the system to ensure scalability, security, and automation throughout the document processing workflow.

---

## Knowledge Gained

After completing the workshop, participants will understand:

- Serverless architecture on AWS.
- The document storage and processing workflow using Amazon S3.
- How to use AWS Lambda to orchestrate the processing workflow.
- How to deploy AI Agents on Amazon Bedrock.
- The process of building a Retrieval-Augmented Generation (RAG) system.
- How to manage data using Amazon DynamoDB.
- Basic security mechanisms on AWS.

---

## Overall Architecture

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.1-Workshop-overview/overview5.1.png" width="1000">
</p>

<p align="center">
<i>Figure 5.1. Overall architecture of the VietAI Scholar Assistant system on AWS.</i>
</p>

---

After completing the **Workshop Overview**, we will continue by preparing the environment and the required resources before deploying the system in the **Prerequisites** section.