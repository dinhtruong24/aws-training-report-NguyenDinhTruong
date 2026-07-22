---
title : "Configure Internet Gateway"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.3.3. </b> "
---

In this section, we will create an **Internet Gateway** and attach it to the `delivery-dev-vpc`.

An Internet Gateway enables resources in the Public Subnets to communicate with the Internet when the Route Table is configured correctly. This is an essential step before configuring the default route for the Public Subnets.

---

## Step 1. Create an Internet Gateway

Sign in to the **AWS Management Console**, open the **VPC** service, and perform the following steps:

1. Select **Internet Gateways** from the left navigation pane.
2. Click **Create internet gateway**.
3. Enter the following Name tag:

```text
delivery-dev-igw
```

4. Click **Create internet gateway**.

After the Internet Gateway is created successfully, it will appear in the resource list with the status indicating that it has not yet been attached to a VPC.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.3-create-internet-gateway.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.7. Creating the delivery-dev-igw Internet Gateway.</i>
</p>

---

## Step 2. Attach the Internet Gateway to the VPC

After creating the Internet Gateway, attach it to the VPC.

Perform the following steps:

1. Select the Internet Gateway:

```text
delivery-dev-igw
```

2. Choose **Actions**.
3. Select **Attach to a VPC**.
4. Under **Available VPCs**, select:

```text
delivery-dev-vpc
```

5. Click **Attach internet gateway**.

Once attached, the Internet Gateway serves as the communication gateway between the VPC and the Internet.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.3-attach-internet-gateway.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.8. Attaching the Internet Gateway to the delivery-dev-vpc.</i>
</p>

---

## Step 3. Verify the Internet Gateway

After the Internet Gateway has been attached successfully, verify the following information:

- **Name:** `delivery-dev-igw`
- **State:** `Attached`
- **VPC:** `delivery-dev-vpc`
- The Internet Gateway is created in the correct Region: `ap-southeast-1`.

Attaching an Internet Gateway to the VPC alone does **not** automatically provide Internet access to the Subnets.

To allow the Public Subnets to access the Internet, a Public Route Table must be created with the following default route:

```text
0.0.0.0/0 → delivery-dev-igw
```

This configuration will be completed in the next section.

---

## Result

After completing this section, you have successfully:

- Created the `delivery-dev-igw` Internet Gateway.
- Attached the Internet Gateway to the `delivery-dev-vpc`.
- Verified that the Internet Gateway is in the **Attached** state.
- Prepared the Internet connectivity gateway for the Public Subnets.

In the next section, we will continue with **5.3.4 – Configure Route Tables** to configure routing for the Public, Application, and Database Subnets.