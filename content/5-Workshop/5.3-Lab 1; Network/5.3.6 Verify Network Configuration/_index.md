---
title : "Verify Network Configuration"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b>5.3.6. </b> "
---

In this section, we will verify the entire network infrastructure deployed in Lab 1, including the VPC, Subnets, Internet Gateway, Route Tables, and NAT Gateway.

The purpose of this verification is to ensure that each network layer is configured correctly, the Public Subnets can access the Internet, and the Private Subnets remain protected from direct external access.

---

## Step 1. Verify the Public Route Table

Open the **VPC** service, select **Route Tables**, and open:

```text
delivery-public-rt
```

Verify the **Routes** tab and confirm that the following routes exist:

```text
10.0.0.0/16 → local
0.0.0.0/0 → delivery-dev-igw
```

Where:

- The **Local Route** allows communication between resources within the VPC.
- The default route `0.0.0.0/0` forwards Internet traffic to the Internet Gateway.

Next, open the **Subnet associations** tab and confirm that the following Public Subnets are associated:

```text
delivery-public-a
delivery-public-b
```

---

## Step 2. Verify the Application Route Table

Open the following Route Table:

```text
delivery-app-rt
```

Verify the **Routes** tab and confirm the following routes:

```text
10.0.0.0/16 → local
0.0.0.0/0 → delivery-nat-a
```

The default route through the NAT Gateway allows resources in the Private Application Subnets to access the Internet through outbound connections without requiring Public IP addresses.

In the **Subnet associations** tab, verify that the following Application Subnets:

```text
delivery-app-a
delivery-app-b
```

are associated with `delivery-app-rt`.

---

## Step 3. Verify the Database Route Table

Open the following Route Table:

```text
delivery-db-rt
```

Verify that the Route Table contains only the Local Route:

```text
10.0.0.0/16 → local
```

There should be **no** routes such as:

```text
0.0.0.0/0 → Internet Gateway
```

or

```text
0.0.0.0/0 → NAT Gateway
```

In the **Subnet associations** tab, confirm that the following Database Subnets:

```text
delivery-db-a
delivery-db-b
```

are associated with `delivery-db-rt`.

Keeping the Database Subnets isolated from direct Internet access improves the security of the database layer.

---

## Step 4. Verify the Public IPv4 Configuration

Open the **Subnets** page and verify the Auto-assign Public IPv4 setting.

The following Public Subnets must have:

```text
Auto-assign public IPv4 address: Enabled
```

Applied to:

```text
delivery-public-a
delivery-public-b
```

The following Private Subnets must have:

```text
Auto-assign public IPv4 address: Disabled
```

Applied to:

```text
delivery-app-a
delivery-app-b
delivery-db-a
delivery-db-b
```

---

## Step 5. Verify Resource Status

Confirm that all network resources are in the expected state:

| Resource | Expected Status |
|---|---|
| `delivery-dev-vpc` | `Available` |
| Six Subnets | `Available` |
| `delivery-dev-igw` | `Attached` |
| `delivery-nat-a` | `Available` |
| `delivery-public-rt` | Route to Internet Gateway configured |
| `delivery-app-rt` | Route to NAT Gateway configured |
| `delivery-db-rt` | Local Route only |

---

## Final Verification Checklist

| Component | Expected Configuration |
|---|---|
| Public Route Table | Local Route and `0.0.0.0/0 → Internet Gateway` |
| Application Route Table | Local Route and `0.0.0.0/0 → NAT Gateway` |
| Database Route Table | Local Route only |
| Public Subnets | Auto-assign Public IPv4 = Enabled |
| Application Subnets | Auto-assign Public IPv4 = Disabled |
| Database Subnets | Auto-assign Public IPv4 = Disabled |

---

## Result

After completing this section, you have successfully:

- Verified the Public Route Table configuration.
- Verified the Application Route Table configuration.
- Verified the Database Route Table configuration.
- Confirmed Internet connectivity for the Public Subnets.
- Confirmed that the Private Application Subnets use the NAT Gateway for outbound Internet access.
- Confirmed that the Private Database Subnets have no direct Internet route.
- Verified the Auto-assign Public IPv4 configuration for all six Subnets.
- Completed the validation of the entire network infrastructure for Lab 1.

After completing **Section 5.3.6**, Lab 1 has been fully deployed and verified. The network infrastructure is now ready for **Lab 2 – Amazon Cognito Authentication**.