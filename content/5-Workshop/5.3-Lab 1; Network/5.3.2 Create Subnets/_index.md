---
title : "Create Subnets"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.3.2. </b> "
---

In this section, we will divide the `delivery-dev-vpc` into six Subnets distributed across two Availability Zones.

The network architecture consists of three layers:

- **Public Subnets:** Used for resources that require direct Internet access, such as the Application Load Balancer and NAT Gateway.
- **Private Application Subnets:** Used for EC2 instances and application services.
- **Private Database Subnets:** Used for Amazon RDS and other database resources.

Distributing the Subnets across two Availability Zones improves the system's availability and fault tolerance.

---

## Step 1. Prepare the Network Address Plan

Create the Subnets according to the following plan:

| Subnet Name | Availability Zone | IPv4 CIDR | Auto-assign Public IPv4 |
|---|---|---|---|
| `delivery-public-a` | `ap-southeast-1a` | `10.0.1.0/24` | Enabled |
| `delivery-public-b` | `ap-southeast-1b` | `10.0.2.0/24` | Enabled |
| `delivery-app-a` | `ap-southeast-1a` | `10.0.11.0/24` | Disabled |
| `delivery-app-b` | `ap-southeast-1b` | `10.0.12.0/24` | Disabled |
| `delivery-db-a` | `ap-southeast-1a` | `10.0.21.0/24` | Disabled |
| `delivery-db-b` | `ap-southeast-1b` | `10.0.22.0/24` | Disabled |

All CIDR blocks must be unique and remain within the VPC CIDR range:

```text
10.0.0.0/16
```

---

## Step 2. Create the Subnets

In the **AWS Management Console**, open the **VPC** service and perform the following steps:

1. Select **Subnets** from the left navigation pane.
2. Click **Create subnet**.
3. Under **VPC ID**, select:

```text
delivery-dev-vpc
```

4. Enter the Subnet name.
5. Select the appropriate Availability Zone.
6. Enter the IPv4 CIDR block according to the network plan.
7. Click **Add new subnet** to define the next Subnet.
8. After configuring all six Subnets, click **Create subnet**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2-create-subnets.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.5. Creating the Subnets and selecting the delivery-dev-vpc.</i>
</p>

---

## Step 3. Configure Auto-assign Public IPv4

After successfully creating all six Subnets, enable automatic Public IPv4 assignment for the two Public Subnets.

Apply this configuration to:

```text
delivery-public-a
delivery-public-b
```

Steps:

1. Select the Public Subnet.
2. Choose **Actions**.
3. Select **Edit subnet settings**.
4. Enable:

```text
Enable auto-assign public IPv4 address
```

5. Click **Save**.

Do **not** enable this option for:

```text
delivery-app-a
delivery-app-b
delivery-db-a
delivery-db-b
```

The Application Subnets and Database Subnets must remain private to prevent direct Internet access.

---

## Step 4. Verify the Subnets

After completing the configuration, verify the following:

- Six Subnets have been created successfully.
- All Subnets are in the `Available` state.
- The Subnets are distributed across two Availability Zones.
- The two Public Subnets have Auto-assign Public IPv4 enabled.
- The Application Subnets and Database Subnets do not have Auto-assign Public IPv4 enabled.
- Each Subnet uses the correct IPv4 CIDR block as defined in the network plan.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2-verify-subnets.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.6. Verifying the six Subnets and the Public IPv4 configuration.</i>
</p>

---

## Result

After completing this section, you have successfully:

- Created two Public Subnets.
- Created two Private Application Subnets.
- Created two Private Database Subnets.
- Distributed the Subnets across two Availability Zones.
- Enabled Auto-assign Public IPv4 for the two Public Subnets.
- Kept the Application Subnets and Database Subnets private.
- Verified that all six Subnets are in the `Available` state.

In the next section, we will continue with **5.3.3 – Configure Internet Gateway** to provide Internet connectivity for the Public Subnets.