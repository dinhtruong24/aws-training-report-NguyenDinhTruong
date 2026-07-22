---
title : "Configure VPC"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.3.1. </b> "
---

# CONFIGURE VPC

In this section, we will create an **Amazon Virtual Private Cloud (VPC)** as the dedicated network foundation for the entire delivery management system on AWS.

The VPC uses the IPv4 CIDR block **10.0.0.0/16**, providing a sufficiently large address space to create Public Subnets, Private Application Subnets, and Private Database Subnets in the following steps.

---

## Step 1. Create an Amazon VPC

Sign in to the **AWS Management Console** and verify that the selected Region is:

```text
Asia Pacific (Singapore) – ap-southeast-1
```

Search for and open the **VPC** service, then perform the following steps:

1. Select **Your VPCs** from the left navigation pane.
2. Click **Create VPC**.
3. Choose **VPC only**.
4. Enter the following Name tag:

```text
delivery-dev-vpc
```

5. Enter the IPv4 CIDR block:

```text
10.0.0.0/16
```

6. Keep the remaining settings as default and click **Create VPC**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-create-vpc.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.2. Creating the VPC with the IPv4 CIDR block 10.0.0.0/16.</i>
</p>

---

## Step 2. Verify the VPC

After the VPC has been created successfully, return to **Your VPCs** and select the newly created VPC.

Verify the following information:

- **Name:** `delivery-dev-vpc`
- **IPv4 CIDR:** `10.0.0.0/16`
- **State:** `Available`
- **Region:** `ap-southeast-1`

Record the **VPC ID**, as it will be required when creating Subnets, Route Tables, Internet Gateways, and other networking resources.

Next, select **Actions** and choose **Edit VPC settings** to configure the DNS options.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-verify-vpc.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.3. Verifying the VPC and opening the DNS configuration settings.</i>
</p>

---

## Step 3. Enable DNS Resolution and DNS Hostnames

In the VPC DNS settings, enable the following options:

```text
Enable DNS resolution
Enable DNS hostnames
```

Then click **Save changes**.

- **DNS Resolution** allows resources inside the VPC to resolve domain names using the Amazon-provided DNS server.
- **DNS Hostnames** enables EC2 instances to receive DNS hostnames when the required networking conditions are met.

These settings are essential for allowing AWS resources within the VPC to communicate with each other and access AWS services using domain names instead of IP addresses.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-enable-dns.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.4. Enabling DNS Resolution and DNS Hostnames for the VPC.</i>
</p>

---

## Result

After completing this section, you have successfully:

- Created the **delivery-dev-vpc** Amazon VPC.
- Configured the IPv4 CIDR block **10.0.0.0/16**.
- Verified that the VPC status is **Available**.
- Recorded the VPC ID for use in the following configuration steps.
- Enabled **DNS Resolution**.
- Enabled **DNS Hostnames**.

The VPC is now ready to be divided into multiple network layers in the next section.

In the following section, we will continue with **5.3.2 – Create Subnets**.