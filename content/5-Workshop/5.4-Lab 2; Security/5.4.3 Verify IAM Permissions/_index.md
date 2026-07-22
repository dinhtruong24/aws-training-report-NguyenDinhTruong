---
title : "Verify IAM Permissions"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.4.3. </b> "
---

In this section, we will verify the IAM Role and IAM Policy configured in the previous section to ensure that the EC2 instance can obtain the correct AWS identity and access the AWS services for which permissions have been granted.

This verification ensures that the IAM Role is functioning correctly, the Runtime IAM Policy has been successfully attached, and the application does not require permanent Access Keys or Secret Access Keys.

---

## Step 1. Attach the IAM Role to the EC2 Instance

Open the **EC2** service in the AWS Management Console and select the EC2 instance that will use the IAM Role.

Perform the following steps:

1. Select the EC2 instance.
2. Choose **Actions**.
3. Select **Security**.
4. Choose **Modify IAM role**.
5. From the IAM Role list, select:

```text
delivery-ec2-role
```

6. Click **Update IAM role**.

After completing this step, the EC2 instance will receive temporary AWS credentials through the IAM Role.

---

## Step 2. Connect to the EC2 Instance

Connect to the EC2 instance using AWS Systems Manager Session Manager or another supported access method.

After signing in successfully, open the terminal and verify that AWS CLI is installed:

```bash
aws --version
```

If AWS CLI is installed correctly, the current version will be displayed.

Do **not** configure permanent credentials using:

```bash
aws configure
```

The EC2 instance should use the temporary credentials provided by the IAM Role.

---

## Step 3. Verify the IAM Identity

Run the following command:

```bash
aws sts get-caller-identity
```

The expected output is similar to:

```json
{
  "UserId": "AROAEXAMPLE:instance-id",
  "Account": "123456789012",
  "Arn": "arn:aws:sts::123456789012:assumed-role/delivery-ec2-role/instance-id"
}
```

Verify that the `Arn` contains the following IAM Role:

```text
delivery-ec2-role
```

If the output displays the correct assumed role, the EC2 instance has successfully obtained temporary credentials from IAM.

---

## Step 4. Verify Amazon S3 Access

Run the following command to verify access to Amazon S3:

```bash
aws s3api head-bucket \
  --bucket <bucket-name> \
  --region ap-southeast-1
```

Replace `<bucket-name>` with the name of your Amazon S3 bucket.

If the command completes without an error, the IAM Role has the required permission to access the bucket.

You can also verify the bucket contents:

```bash
aws s3 ls s3://<bucket-name>/
```

The expected output is a list of folders or objects stored in the bucket.

---

## Step 5. Verify Amazon SQS Access

Run the following command:

```bash
aws sqs get-queue-url \
  --queue-name <queue-name> \
  --region ap-southeast-1
```

Replace `<queue-name>` with the name of your Amazon SQS queue.

The expected output is similar to:

```json
{
  "QueueUrl": "https://sqs.ap-southeast-1.amazonaws.com/123456789012/<queue-name>"
}
```

If the Queue URL is returned successfully, the IAM Role has permission to access Amazon SQS as defined in the Runtime IAM Policy.

---

## Step 6. Verify the Principle of Least Privilege

In addition to verifying the permitted actions, confirm that the IAM Role does not have unnecessary administrative permissions.

In the **AWS Management Console**:

1. Open the **IAM** service.
2. Select **Roles**.
3. Open:

```text
delivery-ec2-role
```

4. Open the **Permissions** tab.
5. Verify that the following policy is attached:

```text
delivery-runtime-policy
```

6. Ensure that broad administrative policies such as:

```text
AdministratorAccess
PowerUserAccess
```

are **not** attached.

The Runtime IAM Policy should grant access only to the AWS services and resources required by the application.

---

## Step 7. Troubleshooting Common Issues

If AWS CLI returns:

```text
Unable to locate credentials
```

verify that:

- The IAM Role is attached to the correct EC2 instance.
- The EC2 instance can access the Instance Metadata Service (IMDS).
- The Trust Relationship allows `ec2.amazonaws.com` to perform `sts:AssumeRole`.

If AWS CLI returns:

```text
AccessDenied
```

verify that:

- The Runtime IAM Policy is attached to the IAM Role.
- The policy includes the required AWS actions.
- The resource ARNs match the actual S3 bucket or SQS queue.
- The correct AWS Region (`ap-southeast-1`) is being used.

---

## Final Verification Checklist

| Verification Item | Expected Result |
|---|---|
| IAM Role attached to EC2 | `delivery-ec2-role` |
| `aws sts get-caller-identity` | Returns a valid assumed role |
| Amazon S3 access | No `AccessDenied` error |
| Amazon SQS access | Queue URL returned successfully |
| Permanent Access Keys | Not used |
| Administrative permissions | Not granted |
| Runtime IAM Policy | Successfully attached |

---

## Result

After completing this section, you have successfully:

- Attached the IAM Role to the EC2 instance.
- Confirmed that the EC2 instance receives temporary AWS credentials.
- Verified the IAM identity using AWS STS.
- Verified access to Amazon S3.
- Verified access to Amazon SQS.
- Confirmed that the Runtime IAM Policy is working correctly.
- Confirmed that the application does not use permanent Access Keys.
- Verified the implementation of the **Principle of Least Privilege**.
- Completed **Lab 2 – Security Groups and IAM**.

After completing **Section 5.4.3**, the system has a secure network configuration and appropriate AWS access permissions. The environment is now ready for **Lab 3 – Amazon S3 Storage**.