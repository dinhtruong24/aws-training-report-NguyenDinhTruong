---
title : "Configure Route Tables"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.3.4. </b> "
---

In this section, we will create and configure **Route Tables** for the three network layers of the system:

- Public Subnets
- Private Application Subnets
- Private Database Subnets

Each network layer uses a dedicated Route Table to control network traffic and ensure that resources are placed in the appropriate network tier.

---

## Step 1. Create the Public Route Table

In the **AWS Management Console**, open the **VPC** service and perform the following steps:

1. Select **Route Tables** from the left navigation pane.
2. Click **Create route table**.
3. Enter the following Name tag:

```text
delivery-public-rt
```

4. Under **VPC**, select:

```text
delivery-dev-vpc
```

5. Click **Create route table**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-create-public-route-table.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.9. Creating the delivery-public-rt Route Table.</i>
</p>

---

## Step 2. Add the Default Route to the Internet Gateway

Open the `delivery-public-rt` Route Table, select the **Routes** tab, and perform the following steps:

1. Click **Edit routes**.
2. Click **Add route**.
3. Enter the Destination:

```text
0.0.0.0/0
```

4. Under **Target**, select **Internet Gateway**.
5. Choose:

```text
delivery-dev-igw
```

6. Click **Save changes**.

This route allows resources in the Public Subnets to access the Internet through the Internet Gateway.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-configure-public-route.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.10. Adding the default route (0.0.0.0/0) through the Internet Gateway.</i>
</p>

---

## Step 3. Associate the Public Subnets

In the `delivery-public-rt` Route Table, open the **Subnet associations** tab and perform the following steps:

1. Click **Edit subnet associations**.
2. Select the two Public Subnets:

```text
delivery-public-a
delivery-public-b
```

3. Click **Save associations**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-associate-public-subnets.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.11. Associating the two Public Subnets with the Public Route Table.</i>
</p>

After saving the configuration, verify that both Public Subnets are correctly associated with the `delivery-public-rt` Route Table.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-verify-public-route-table.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.12. Verifying the Public Subnet associations.</i>
</p>

---

## Step 4. Create the Private Application Route Table

Next, create a Route Table for the Private Application Subnets.

1. Click **Create route table**.
2. Enter the following Name tag:

```text
delivery-app-rt
```

3. Select the VPC:

```text
delivery-dev-vpc
```

4. Click **Create route table**.
5. Open the **Subnet associations** tab.
6. Associate the two Application Subnets:

```text
delivery-app-a
delivery-app-b
```

This Route Table will be updated with a default route through the NAT Gateway in **Section 5.3.5**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-create-private-route-table.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.13. Creating the delivery-app-rt Route Table and associating the Application Subnets.</i>
</p>

Verify that the Route Table currently contains only the **Local Route** before adding the NAT Gateway route.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-verify-private-route-table.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.14. Verifying the Application Route Table before adding the NAT Gateway route.</i>
</p>

---

## Step 5. Create the Database Route Table

Create a dedicated Route Table for the Private Database Subnets.

1. Click **Create route table**.
2. Enter the following Name tag:

```text
delivery-db-rt
```

3. Select the VPC:

```text
delivery-dev-vpc
```

4. Click **Create route table**.
5. Open the **Subnet associations** tab.
6. Associate the two Database Subnets:

```text
delivery-db-a
delivery-db-b
```

The Database Route Table should contain only the **Local Route**. Do not add an Internet Gateway or NAT Gateway route to prevent direct Internet access to the database layer.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-create-database-route-table.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.15. Creating the delivery-db-rt Route Table and associating the Database Subnets.</i>
</p>

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-associate-database-subnets.png" width="900">
</p>

<p align="center">
<i>Figure 5.3.16. Verifying the Database Subnet associations.</i>
</p>

---

## Step 6. Verify the Route Tables

After completing the configuration, verify the following Route Tables:

| Route Table | Associated Subnets | Routes |
|---|---|---|
| `delivery-public-rt` | `delivery-public-a`, `delivery-public-b` | Local Route and `0.0.0.0/0 → delivery-dev-igw` |
| `delivery-app-rt` | `delivery-app-a`, `delivery-app-b` | Local Route; the NAT Gateway route will be added in the next section |
| `delivery-db-rt` | `delivery-db-a`, `delivery-db-b` | Local Route only |

Ensure that each Subnet is associated with the correct Route Table based on its network layer.

---

## Result

After completing this section, you have successfully:

- Created the `delivery-public-rt` Route Table.
- Added the default route through the Internet Gateway.
- Associated the two Public Subnets with the Public Route Table.
- Created the `delivery-app-rt` Route Table.
- Associated the two Application Subnets with the Application Route Table.
- Created the `delivery-db-rt` Route Table.
- Associated the two Database Subnets with the Database Route Table.
- Kept the Database Route Table configured with only the Local Route.

In the next section, we will continue with **5.3.5 – Create NAT Gateway** and configure the default route for the Private Application Subnets.