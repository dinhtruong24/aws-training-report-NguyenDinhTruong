---
title : "Configure IAM Role and IAM Policy"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.4.2. </b> "
---

In this section, we will create an **IAM Role** for Amazon EC2 and configure an **IAM Policy** that allows the application to access the required AWS services during runtime.

Using an IAM Role enables EC2 instances to obtain temporary AWS credentials without storing Access Keys or Secret Access Keys directly in the application source code or configuration files.

---

## Step 1. Create an IAM Role for EC2

Sign in to the **AWS Management Console** and open the **IAM** service.

Perform the following steps:

1. Select **Roles** from the left navigation pane.
2. Click **Create role**.
3. Under **Trusted entity type**, select:

```text
AWS service
```

4. Under **Use case**, select:

```text
EC2
```

5. Click **Next**.
6. Continue to the role naming step.
7. Enter the IAM Role name:

```text
delivery-ec2-role
```

8. Enter the description:

```text
IAM Role for the delivery application EC2 instances
```

9. Review the configuration and click **Create role**.

This IAM Role will be attached to the EC2 instances in the deployment phase of the application.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-create-iam-role.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.4. Creating an IAM Role for EC2 instances.</i>
</p>

---

## Step 2. Verify the IAM Role

After the IAM Role has been created successfully, open the following role:

```text
delivery-ec2-role
```

Verify the following information:

- **Role name:** `delivery-ec2-role`
- **Trusted entity:** `ec2.amazonaws.com`
- **Use case:** EC2
- The role is created in the correct AWS account.
- The role does not contain permanent Access Keys.

In the **Trust relationships** tab, verify that EC2 is allowed to assume the role using:

```text
sts:AssumeRole
```

The Trust Policy should look similar to the following:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "ec2.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-verify-iam-role.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.5. Verifying the IAM Role and Trust Relationship for EC2.</i>
</p>

---

## Step 3. Create the Runtime IAM Policy

Next, create an IAM Policy that grants the application the required permissions during runtime.

In the **IAM** service, perform the following steps:

1. Select **Policies**.
2. Click **Create policy**.
3. Open the **JSON** tab.
4. Enter the policy document that defines the required permissions.
5. Click **Next**.
6. Enter the policy name:

```text
delivery-runtime-policy
```

7. Enter the description:

```text
Runtime permissions for the delivery application
```

8. Review the configuration and click **Create policy**.

The policy may include permissions for services such as Amazon S3, Amazon SQS, and other AWS services required by the application.

Example policy structure:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "S3ObjectAccess",
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::delivery-*",
        "arn:aws:s3:::delivery-*/*"
      ]
    },
    {
      "Sid": "SQSAccess",
      "Effect": "Allow",
      "Action": [
        "sqs:GetQueueUrl",
        "sqs:GetQueueAttributes",
        "sqs:SendMessage",
        "sqs:ReceiveMessage",
        "sqs:DeleteMessage"
      ],
      "Resource": "arn:aws:sqs:ap-southeast-1:*:delivery-*"
    }
  ]
}
```

> **Note:** In a production environment, replace wildcard (`*`) resources with the specific resource ARNs to follow the **Principle of Least Privilege**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-create-runtime-policy.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.6. Creating the Runtime IAM Policy.</i>
</p>

---

## Step 4. Attach the IAM Policy to the IAM Role

After creating the policy, attach it to the `delivery-ec2-role`.

Perform the following steps:

1. Open the **IAM** service.
2. Select **Roles**.
3. Open:

```text
delivery-ec2-role
```

4. In the **Permissions** tab, click **Add permissions**.
5. Select **Attach policies**.
6. Search for:

```text
delivery-runtime-policy
```

7. Select the policy.
8. Click **Add permissions**.

After completing this step, the IAM Role will have the permissions required for the EC2 instances to access the AWS services defined in the Runtime Policy.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-attach-policy-to-role.png" width="900">
</p>

<p align="center">
<i>Figure 5.4.7. Attaching the Runtime IAM Policy to the EC2 IAM Role.</i>
</p>

---

## Step 5. Verify the IAM Role Permissions

Open the `delivery-ec2-role` again and review the **Permissions** tab.

Verify that the following policy is attached:

```text
delivery-runtime-policy
```

Also confirm that:

- The role has the correct Trust Relationship for EC2.
- The Runtime IAM Policy is successfully attached.
- No broad administrative permissions such as `AdministratorAccess` are granted.
- Permissions are limited to only the AWS services and resources required by the application.
- No permanent Access Keys are used by the application.

---

## Result

After completing this section, you have successfully:

- Created the `delivery-ec2-role` IAM Role.
- Configured EC2 as the trusted entity.
- Verified the IAM Role Trust Relationship.
- Created the `delivery-runtime-policy` IAM Policy.
- Configured runtime permissions for the required AWS services.
- Attached the Runtime IAM Policy to the IAM Role.
- Applied the **Principle of Least Privilege**.
- Prepared the IAM Role to be attached to EC2 instances in the following labs.

In the next section, we will continue with **5.4.3 – Verify IAM Permissions** using the AWS CLI.