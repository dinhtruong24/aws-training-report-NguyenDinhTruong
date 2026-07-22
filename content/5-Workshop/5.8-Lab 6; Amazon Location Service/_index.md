---
title : "Lab 6: Amazon Location Service"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b>5.8. </b> "
---

In this lab, we will explore **Amazon Location Service**, an AWS service that enables applications to integrate maps, place search, routing, and location tracking capabilities.

Amazon Location Service provides APIs and SDKs that allow developers to build location-aware applications with secure access to mapping, geocoding, routing, and tracking services. It simplifies the implementation of geospatial features while integrating seamlessly with other AWS services.

In this lab, we will configure Amazon Location Service and verify the required resources to prepare the environment for integrating location-based features into the application.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.8-lab6/5.8.1-configure-amazon-location.png" width="900">
</p>

<p align="center">
<i>Figure 5.8.1. Configuring Amazon Location Service.</i>
</p>

---

## Lab Objectives

After completing this lab, you will be able to:

- Access Amazon Location Service.
- Configure Amazon Location resources.
- Explore the Amazon Location management console.
- Prepare the environment for integrating maps and location services into an application.

---

## Service Architecture

In this lab, Amazon Location Service is organized as follows:

```text
Application
      │
      ▼
Amazon Location Service
      │
      ├── Maps
      ├── Places
      ├── Routes
      └── Trackers
```

Amazon Location Service provides location-based capabilities that enable applications to display maps, search for places, calculate routes, and manage location tracking.

---

## Main Components

This lab uses the following components:

| Component | Description |
|---|---|
| Amazon Location Service | AWS location service |
| Maps | Map visualization |
| Places | Place search |
| Routes | Route calculation |
| Trackers | Device location tracking |

---

## Lab Contents

Lab 6 consists of one section:

### 5.8.1 Configure Amazon Location

In this section, we will:

- Access Amazon Location Service.
- Configure the required resources.
- Verify the configuration after deployment.

---

## Expected Results

After completing Lab 6:

- Amazon Location Service has been configured successfully.
- The required location resources are ready for use.
- The environment is prepared for integrating maps and location-based features into the application.

After completing Lab 6, we will continue with **Lab 7**.