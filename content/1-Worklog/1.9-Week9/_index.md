---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}


### Week 9 Objectives:

* Master applied AI systems by gathering deep hands-on expertise with AWS cognitive speech services (comprising Text-to-Speech and Speech-to-Text capabilities) alongside managed computer vision engines.
* Investigate Generative AI concepts and Large Language Models (LLMs), acquiring structural frameworks for deploying and embedding LLM components within production enterprise software.
* Explore the end-to-end cloud machine learning platform Amazon SageMaker, navigating the managed Jupyter Notebook infrastructure to build, clean, and orchestrate ML models.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Surveyed speech processing architecture blueprints leveraging Amazon Polly and Amazon Transcribe; tested Polly capabilities to convert textual data into realistic vocal outputs across diverse languages, and integrated Transcribe to decode spoken audio resources back into accurate text documents.    | 29/06/2026 | 29/06/2026      | 	https://000072.awsstudygroup.com/ https://000073.awsstudygroup.com/ |
| Tuesday  | - Analyzed corporate LLM implementation architectures; studied engineering patterns required to integrate Large Language Models into enterprise production systems, focusing heavily on Retrieval-Augmented Generation (RAG) concepts to safely read proprietary internal knowledge repositories.  | 30/06/2026 | 30/06/2026      | https://000105.awsstudygroup.com/ https://000106.awsstudygroup.com/ |
| Wednesday  | - Explored the infrastructure layout of the Amazon SageMaker ecosystem; analyzed this comprehensive E2E ML platform by examining its structural building blocks, including SageMaker Studio workspace configurations, managed Notebook Instances, built-in cloud algorithms, and real-time model Endpoint serving. | 01/07/2026 | 01/07/2026      | https://000200.awsstudygroup.com/ |
| Thursday  | - Automated image categorization workflows utilizing custom Python scripts and Amazon Rekognition; coded a programmatic interface that mounts to Amazon S3 buckets, invoking Rekognition APIs to analyze batches of graphic media and generate metadata tags automatically.   | 02/07/2026 | 02/07/2026      | https://000200.awsstudygroup.com/ |
| Friday  | - Completed Technical Blog 1 & Blog 2 write-ups, and tested interactive model training cycles using a SageMaker Notebook Instance; launched a managed Jupyter environment, processed and normalized training datasets, and executed the final pipeline to train a baseline classification model.    | 08/15/2025 | 08/15/2025      | https://000200.awsstudygroup.com/ |


### Week 9 Achievements:

* Managed Audio & Computer Vision Mastery: Designed operational text-to-speech and speech-to-text workflows using Polly and Transcribe, while deploying a functional Python architecture that automates high-volume image ingestion and tag processing via Amazon Rekognition.

* GenAI Infrastructure & RAG Strategy Comprehension: Acquired the architectural foundations needed to dock LLMs within real-world application pipelines, mastering RAG data-fetching designs to protect proprietary company information.

* Production ML Pipeline Implementation: Gained intermediate proficiency in managing Amazon SageMaker environments, successfully executing remote dataset preprocessing and classification algorithm training while delivering the technical documentation for both structural Blogs.

### Week 9 Evaluation:
* On Friday, while performing intensive matrix transformations and data cleaning routines over a large validation dataset directly inside the SageMaker Notebook environment, the runtime instance crashed due to an Out-of-Memory (OOM) error from undersized default compute provisions. This offered a critical real-world lesson regarding data science hardware scoping. I successfully resolved the bottleneck by stopping the instance to upscale its underlying hardware classification, while simultaneously refactoring the ingestion scripts to stream and transform the data matrix in smaller iterative batches.
