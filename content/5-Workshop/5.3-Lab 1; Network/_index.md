---
title : "Lab 1: Network Infrastructure"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.3. </b> "
---

The first lab focuses on building the network infrastructure for the entire system on AWS. This is a fundamental step to establish a secure, isolated, and scalable networking environment for all application components.

In this lab, we will deploy an **Amazon Virtual Private Cloud (VPC)** using a multi-tier architecture. The environment includes Public Subnets and Private Subnets distributed across two Availability Zones to improve system availability and fault tolerance.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-network/5.3.1-network-plan.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.1. Network architecture and CIDR planning for the system.</i>
</p>

---

## Lab Objectives

After completing this lab, you will be able to:

- Create an Amazon VPC for the system.
- Configure DNS Resolution and DNS Hostnames.
- Create Public Subnets and Private Subnets.
- Configure an Internet Gateway.
- Create Route Tables for different network layers.
- Deploy a NAT Gateway to provide Internet access for Private Subnets.
- Verify the complete network configuration before deploying additional AWS services.

---

## Lab Contents

This lab is divided into the following sections:

1. **5.3.1 Configure VPC**
   - Create an Amazon VPC.
   - Verify the VPC configuration.
   - Enable DNS Resolution and DNS Hostnames.

2. **5.3.2 Create Subnets**
   - Create Public Subnets.
   - Create Private Application Subnets.
   - Create Private Database Subnets.

3. **5.3.3 Configure Internet Gateway**
   - Create an Internet Gateway.
   - Attach the Internet Gateway to the VPC.

4. **5.3.4 Configure Route Tables**
   - Create a Public Route Table.
   - Create a Private Application Route Table.
   - Create a Database Route Table.
   - Associate Route Tables with the corresponding Subnets.

5. **5.3.5 Create NAT Gateway**
   - Create a NAT Gateway.
   - Verify Internet connectivity for the Private Subnets.

---

After completing Lab 1, the network infrastructure will be fully prepared for deploying the security, storage, database, event-driven, location, and compute components in the following labs.