---
title : "Create NAT Gateway"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b>5.3.5. </b> "
---

In this section, we will create a **NAT Gateway** to allow resources in the Private Application Subnets to access the Internet through outbound connections without assigning Public IP addresses.

The NAT Gateway will be deployed in the `delivery-public-a` Public Subnet and associated with an Elastic IP. After that, the `delivery-app-rt` Route Table will be updated to route Internet-bound traffic from the Application Subnets through the NAT Gateway.

---

## Step 1. Create a NAT Gateway

In the **AWS Management Console**, open the **VPC** service and perform the following steps:

1. Select **NAT Gateways** from the left navigation pane.
2. Click **Create NAT gateway**.
3. Enter the following Name tag:

```text
delivery-nat-a
```

4. Under **Subnet**, select:

```text
delivery-public-a
```

5. Under **Connectivity type**, select:

```text
Public
```

6. Click **Allocate Elastic IP** to allocate a new Elastic IP address.
7. Click **Create NAT gateway**.

The NAT Gateway must be deployed in a Public Subnet because it uses the Internet Gateway to forward outbound Internet traffic.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.5-create-nat-gateway.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.17. Creating the delivery-nat-a NAT Gateway in the delivery-public-a Public Subnet.</i>
</p>

---

## Step 2. Wait for the NAT Gateway to Become Available

After creating the NAT Gateway, monitor its status.

Wait until the status changes to:

```text
Available
```

Then verify the following information:

- **Name:** `delivery-nat-a`
- **Subnet:** `delivery-public-a`
- **Connectivity type:** `Public`
- **Elastic IP:** Allocated
- **State:** `Available`

Do not configure the Route Table until the NAT Gateway reaches the **Available** state.

---

## Step 3. Update the Application Route Table

Open the following Route Table:

```text
delivery-app-rt
```

Then perform these steps:

1. Open the **Routes** tab.
2. Click **Edit routes**.
3. Click **Add route**.
4. Enter the Destination:

```text
0.0.0.0/0
```

5. Under **Target**, select **NAT Gateway**.
6. Choose:

```text
delivery-nat-a
```

7. Click **Save changes**.

After the configuration is complete, the Application Route Table should contain the following routes:

```text
10.0.0.0/16 → local
0.0.0.0/0 → delivery-nat-a
```

This route allows EC2 instances in the Private Application Subnets to download packages, update software, and access external services without requiring Public IP addresses.

---

## Step 4. Keep the Database Route Table Private

Do **not** add a NAT Gateway route to the following Route Table:

```text
delivery-db-rt
```

The Database Route Table should contain only the Local Route:

```text
10.0.0.0/16 → local
```

This configuration prevents the database layer from having direct Internet access, reducing the attack surface and improving the security of Amazon RDS instances in the Private Database Subnets.

---

## Step 5. Verify the Network Configuration

After completing the NAT Gateway configuration, verify the following Route Tables:

| Route Table | Expected Routes |
|---|---|
| `delivery-public-rt` | Local Route and `0.0.0.0/0 → delivery-dev-igw` |
| `delivery-app-rt` | Local Route and `0.0.0.0/0 → delivery-nat-a` |
| `delivery-db-rt` | Local Route only |

Also confirm that:

- The two Public Subnets are associated with `delivery-public-rt`.
- The two Application Subnets are associated with `delivery-app-rt`.
- The two Database Subnets are associated with `delivery-db-rt`.
- The Public Subnets have Auto-assign Public IPv4 enabled.
- The Application Subnets and Database Subnets do not have Auto-assign Public IPv4 enabled.

---

> **Note:** A NAT Gateway incurs charges based on running time and data processing. After completing the workshop, it is recommended to delete the NAT Gateway and release the Elastic IP if they are no longer needed.

---

## Result

After completing this section, you have successfully:

- Created the `delivery-nat-a` NAT Gateway.
- Deployed the NAT Gateway in the `delivery-public-a` Public Subnet.
- Allocated an Elastic IP for the NAT Gateway.
- Verified that the NAT Gateway is in the **Available** state.
- Added the default route from `delivery-app-rt` to the NAT Gateway.
- Enabled outbound Internet access for the Private Application Subnets.
- Kept the Database Route Table configured with only the Local Route.
- Completed the network infrastructure for Lab 1.

After completing **Section 5.3.5**, the network foundation—including the VPC, Subnets, Internet Gateway, Route Tables, and NAT Gateway—is fully configured and ready for the next labs.