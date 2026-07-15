---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Master the data engineering lifecycle by exploring automated ETL (Extract, Transform, Load) pipelines and constructing highly-responsive real-time log aggregation infrastructures.
* Acquire core structural principles for engineering scalable Cloud Data Lakes to facilitate central data consolidation and prepare for predictive future analytics.
* Venture into applied AI/ML operations by embedding native AWS cognitive computing services directly into existing architectures without training custom neural network models.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Conducted a deep dive into AWS Data Pipeline and foundational ETL architectures; analyzed backend pipeline components to construct an automated ETL process designed to securely transfer and reshape datasets across heterogeneous storage layers.     | 22/06/2026 | 22/06/2026      | https://000113.awsstudygroup.com/ https://00012.awsstudygroup.com/ |
| Tuesday  | - Developed a live telemetry ingestion platform utilizing Amazon Kinesis; provisioned Kinesis Data Streams instances and programmed a prototype web application that constantly emits mock system logs to test real-time event stream processing.   | 23/06/2026 | 23/06/2026      | https://000040.awsstudygroup.com/ https://000053.awsstudygroup.com/ |
| Wednesday  | - Implemented automated data replication from Amazon DynamoDB over to Amazon S3; leveraged AWS Data Pipeline to orchestrate scheduled table exports, securing historical NoSQL snapshots in S3 buckets for robust disaster recovery and analytics readiness. | 24/06/2026 | 24/06/2026      | https://000060.awsstudygroup.com/ |
| Thursday  | - Investigated cloud-native centralized repository designs through Cloud Data Lake architectures; learned how to mount a unified Data Lake on Amazon S3, managing metadata mapping and categorizing stored data into Raw, Cleaned, and Curated structural layers.   | 25/06/2026 | 25/06/2026      | https://000035.awsstudygroup.com/ https://000070.awsstudygroup.com/ |
| Friday  | - Explored advanced computer vision applications powered by Amazon Rekognition; experimented with managed APIs to implement face validation, human emotion analysis, object detection boundaries, and image-based text extraction (OCR).     | 26/06/2026 | 26/06/2026      | https://000135.awsstudygroup.com/ https://000066.awsstudygroup.com/ |


### Week 8 Achievements:

* Automated Data Flows & ETL Integration: Successfully engineered automated ETL workflows via AWS Data Pipeline and deployed a responsive real-time event-driven logging layer combining a simulated web app with Kinesis Data Streams.

* Unified Data Lake Storage Architecture: Attained practical skills in staging multi-layered object storage inside Amazon S3 and effectively configured automated scheduler jobs to dump NoSQL DynamoDB backups securely.

* Cognitive AI Service Implementation: Mastered production-ready APIs within the Amazon Rekognition engine, establishing immediate capabilities for programmatic computer vision (OCR and object parsing) without infrastructure overhead.

### Week 8 Evaluation:
* During Wednesday's operational task of backing up high-volume tables from DynamoDB to Amazon S3 using AWS Data Pipeline, the system initially spiked the database Read Capacity Units (RCU), degrading live application response latency. This provided an invaluable architectural lesson on data engineering resource throttling. I successfully mitigated the production bottleneck by adjusting the read throughput ratio parameter inside the pipeline settings, ensuring consistent background data transfers without starving the operational database layer.
