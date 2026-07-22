---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### Overview

This workshop provides a step-by-step guide to building **VietAI Scholar Assistant**, an AI-powered academic assistant developed on the AWS Cloud platform. The system enables users to upload one or multiple PDF documents for automatic analysis, translation, summarization, context-aware question answering, and knowledge assessment based on the uploaded content.

Throughout this workshop, participants will learn how to develop an end-to-end document processing workflow, including document storage, content extraction, Large Language Model (LLM) processing, embedding generation, Retrieval-Augmented Generation (RAG), and AI agent orchestration using Amazon Bedrock.

In addition, the workshop demonstrates how multiple AWS services can be integrated within a serverless architecture to provide scalability, reliability, and cost efficiency. The entire solution is designed on AWS and can be extended to support various real-world AI-powered document processing applications.

---

#### Architecture Highlights

- **Frontend:** A React-based web application that allows users to upload PDF documents, view processing results, and interact with the AI assistant.
- **Document Storage:** Amazon S3 is used to securely store uploaded documents, generated outputs, and intermediate processing files.
- **Backend:** Amazon API Gateway and AWS Lambda receive user requests and orchestrate the entire document processing workflow.
- **AI Processing:** Amazon Bedrock and AI Agents perform document analysis, translation, summarization, and context-aware question answering.
- **OCR & Document Understanding:** The system supports processing complex documents containing scanned pages, mathematical formulas, charts, and images to ensure accurate document understanding.
- **Retrieval-Augmented Generation (RAG):** Processed documents are converted into embeddings and indexed to provide semantic search and document-based question answering.
- **Database:** Amazon DynamoDB stores document metadata, processing status, and application information required during execution.
- **Security:** AWS IAM and Amazon Cognito provide identity management, authentication, and secure access to AWS resources.
- **Automation:** The complete workflow is automatically triggered through Amazon S3 events and AWS Lambda, minimizing manual operations.

---

#### Content

1. [Workshop overview](5.1-Workshop-overview)
2. [Prerequiste](5.2-Prerequiste/)
3. [Access S3 from VPC](5.3-S3-vpc/)
4. [Access S3 from On-premises](5.4-S3-onprem/)
5. [VPC Endpoint Policies (Bonus)](5.5-Policy/)
6. [Clean up](5.6-Cleanup/)

---

## Learning Objectives

After completing this workshop, participants will be able to:

- Understand the architecture of an AI-powered document processing system built on AWS.
- Deploy a document storage solution using Amazon S3.
- Build AI Agents with Amazon Bedrock for document analysis and intelligent interaction.
- Develop a Retrieval-Augmented Generation (RAG) pipeline for context-aware question answering.
- Manage document metadata and processing status using Amazon DynamoDB.
- Apply AWS security services to protect cloud resources and user data.
- Gain practical experience in deploying modern AI applications using a serverless architecture on AWS.

---

## System Architecture

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/Workshop.png" width="900">
</p>