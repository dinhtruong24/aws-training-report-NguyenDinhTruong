---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
#### Overview

This workshop focuses on building the **VietAI Scholar Assistant**, an AI-powered academic assistant that leverages Large Language Models (LLMs) and AWS Cloud services. The platform enables users to upload one or multiple PDF documents, automatically translate, summarize, analyze academic papers, and interact with the documents through Retrieval-Augmented Generation (RAG).

During the workshop, participants learn how to integrate modern AWS services to develop a complete AI application, covering document storage, serverless orchestration, AI processing pipelines, vector search, and multi-agent collaboration using Amazon Bedrock.

In addition to text processing, the system is capable of understanding mathematical formulas, charts, and images, then exporting the processed content into Markdown or HTML. This significantly improves the efficiency of studying and researching academic materials.

#### Architecture Highlights

- **Frontend:** Built with React, hosted on Amazon S3, and globally distributed through Amazon CloudFront.
- **Backend:** Amazon API Gateway and AWS Lambda are used to receive requests and orchestrate the serverless processing workflow.
- **AI Processing:** Amazon Bedrock Agents coordinate the Supervisor Agent, Document Agent, and Researcher Agent for intelligent document analysis.
- **Multimodal Processing:** Claude 3.5 Sonnet extracts text, translates content, recognizes mathematical formulas, and interprets diagrams.
- **OCR Backup:** Amazon Textract is utilized when scanned documents or low-quality PDFs require OCR processing.
- **Retrieval-Augmented Generation (RAG):** Titan Text Embeddings together with Amazon S3 Vectors provide semantic search and document-based question answering.
- **Storage:** Amazon S3 stores original PDF files, Markdown/HTML outputs, and vector data, while Amazon DynamoDB manages metadata and processing status.
- **Security:** AWS IAM, Amazon Cognito, Amazon S3 Bucket Policies, and AWS KMS protect user data and control system access.
- **Automation:** Amazon S3 Event Notifications automatically trigger AWS Lambda whenever a new document is uploaded.

#### System Workflow

Users upload one or more PDF documents through the React-based web interface. The application requests a presigned URL from Amazon API Gateway and uploads the files directly to Amazon S3.
Once a document is uploaded, Amazon S3 Event Notification automatically invokes the AWS Lambda Orchestrator. Lambda forwards the document information to the Supervisor Agent running on Amazon Bedrock, which determines the appropriate processing workflow.
For standard PDF documents, the Document Agent uses Claude 3.5 Sonnet to extract text, interpret formulas, analyze images, and understand document structure. If the uploaded file is a scanned document with poor quality, Amazon Textract is used as an OCR fallback service.
After processing is completed, the extracted information is formatted into structured JSON, converted into Markdown or HTML, stored back in Amazon S3, and the processing status is updated in Amazon DynamoDB. Finally, the generated result is returned to users through REST APIs or WebSocket connections.

#### Content

1. [Workshop overview](5.1-Workshop-overview)
2. [Prerequiste](5.2-Prerequiste/)
3. [Access S3 from VPC](5.3-S3-vpc/)
4. [Access S3 from On-premises](5.4-S3-onprem/)
5. [VPC Endpoint Policies (Bonus)](5.5-Policy/)
6. [Clean up](5.6-Cleanup/)

<p align="center">
  <img
    src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/Workshop.png"
    width="850"
    alt="VietAI Scholar Assistant Workshop Architecture">
</p>