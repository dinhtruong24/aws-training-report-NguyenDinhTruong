---
title : "Configure the S3 Gateway Endpoint"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.5.3. </b> "
---

In this section, we will configure an **Amazon S3 Gateway Endpoint** to allow resources inside the VPC to access Amazon S3 through the AWS private network without using an Internet Gateway or NAT Gateway.

Using a Gateway Endpoint improves security, reduces data transfer costs, and provides a more efficient connection between EC2 instances and Amazon S3.

---

## Step 1. Open the Amazon VPC Service

Sign in to the **AWS Management Console**.

Perform the following steps:

1. Search for the **VPC** service.
2. Select **Endpoints**.
3. Click **Create endpoint**.

---

## Step 2. Create the S3 Gateway Endpoint

On the **Create endpoint** page, configure the following settings:

**Service category**

```text
AWS services
```

**Service**

```text
com.amazonaws.ap-southeast-1.s3
```

**Endpoint type**

```text
Gateway
```

**VPC**

```text
delivery-dev-vpc
```

Next, select the appropriate **Route Tables** to associate with the Gateway Endpoint.

After completing the configuration, click **Create endpoint**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.5-lab3/5.5.3-create-s3-gateway-endpoint.png" width="900">
</p>

<p align="center">
<i>Figure 5.5.4. Creating the Amazon S3 Gateway Endpoint.</i>
</p>

---

## Step 3. Verify the Gateway Endpoint

After the endpoint has been created successfully:

- Open the **Endpoints** list.
- Verify that the endpoint status is **Available**.
- Confirm that the endpoint is associated with the correct Route Tables.
- Verify that the Service Name is:

```text
com.amazonaws.ap-southeast-1.s3
```

At this point, EC2 instances within the VPC can access Amazon S3 through the AWS private network.

---

## Configuration Summary

| Property | Value |
|---|---|
| AWS Service | Amazon S3 |
| Endpoint Type | Gateway |
| Service Name | `com.amazonaws.ap-southeast-1.s3` |
| VPC | `delivery-dev-vpc` |
| Status | Available |

---

## Result

After completing this section, you have successfully:

- Created an Amazon S3 Gateway Endpoint.
- Associated the endpoint with the appropriate Route Tables.
- Enabled EC2 instances to access Amazon S3 through the AWS private network.
- Eliminated the need to access Amazon S3 over the public Internet.
- Completed the storage configuration for Lab 3.

After completing **Section 5.5.3**, the system has a complete storage environment and is ready for **Lab 4 – CloudWatch Monitoring**.