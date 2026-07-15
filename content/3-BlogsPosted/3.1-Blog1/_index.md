---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Protecting Amazon RDS Credentials for AWS Lambda with AWS Secrets Manager

In serverless applications, AWS Lambda functions often need to access a database to read or process application data. An insecure implementation is to store database usernames and passwords directly in source code or Lambda environment variables. This approach increases the risk of exposing sensitive information through shared code, configuration access, or application logs.

A more secure solution is to store the database credentials in **AWS Secrets Manager**. When the Lambda function needs to connect to Amazon RDS, it retrieves the secret at runtime through the Secrets Manager API. As a result, the password does not need to appear directly in the application source code.

## Solution Architecture

The request flow works as follows:

1. A client sends a request to a REST API hosted by Amazon API Gateway.
2. API Gateway invokes an AWS Lambda function.
3. The Lambda function uses its IAM role to request the database secret from AWS Secrets Manager.
4. Secrets Manager returns the protected username and password.
5. Lambda uses the credentials to connect to Amazon RDS for MySQL.
6. The query result is returned to the client through API Gateway.

## Main Components
### Amazon API Gateway

Amazon API Gateway provides the REST API endpoint used by clients. It forwards incoming requests to Lambda without storing database credentials.

### AWS Lambda

The Lambda function contains the application logic. Before connecting to the database, it calls the Secrets Manager GetSecretValue API to retrieve the required credentials.
The Lambda execution role should only have permission to access the specific secret required by the application.

### AWS Secrets Manager

Secrets Manager stores the database username and password as an encrypted secret. The Lambda function retrieves this information only when it needs to establish a database connection.

### Amazon RDS

Amazon RDS for MySQL stores the application data. The database should not be publicly accessible and should only accept connections from authorized resources.

### AWS CloudFormation

AWS CloudFormation automates the deployment of the following resources:

- Amazon RDS.
- AWS Secrets Manager.
- AWS Lambda.
- Amazon API Gateway.
- IAM roles and policies.

CloudFormation uses a dynamic reference to retrieve the database password from Secrets Manager during deployment. This prevents the resolved password from being stored directly in the template or deployment logs.

### Secret Rotation

AWS Secrets Manager can automatically rotate the database password according to a defined schedule, such as every 30 days.

During rotation, a Lambda rotation function performs the following actions:

1. Generates a new password.
2. Updates the password in Amazon RDS.
3. Stores the new value in Secrets Manager.
4. Tests the new credentials.
5. Marks the new secret version as current.

The application does not require source-code changes after the password is rotated because Lambda always retrieves the latest secret value.

### Testing the Solution

After the CloudFormation stack has been deployed, the API endpoint can be opened from the stack Outputs section.

When a request is sent:

- API Gateway invokes Lambda.
- Lambda retrieves the secret from Secrets Manager.
- Lambda connects to the RDS MySQL database.
- The database query is executed.
- The result is returned to the client.

The Lambda environment variables should not contain the database password. They should only contain non-sensitive configuration values such as the secret name, RDS endpoint, database name, and username.

### Benefits
- Removes hardcoded passwords from source code.
- Reduces the exposure of secrets through environment variables.
- Supports automatic credential rotation.
- Controls access through IAM policies.
- Automates infrastructure deployment with CloudFormation.
- Improves database security for serverless applications.
- Reduces manual credential-management tasks.

### Conclusion

Combining AWS Lambda, AWS Secrets Manager, and Amazon RDS provides a safer way for serverless applications to access databases. Secrets Manager controls the lifecycle of the database credentials, while Lambda retrieves the secret only when required.

This approach eliminates hardcoded passwords, supports automatic rotation, and improves access control across the AWS environment.

<p align="center">
  <img
    src="/images/3-BlogsPosted/blog1-architecture.png"
    width="700"
    alt="AWS Secrets Manager Architecture">
</p>

<p align="center">
  <em>Figure 1. Architecture for securely managing Amazon RDS database credentials with AWS Secrets Manager.</em>
</p>

<p align="center">
  <strong>Reference Article:</strong>
  <a href="https://aws.amazon.com/blogs/security/how-to-securely-provide-database-credentials-to-lambda-functions-by-using-aws-secrets-manager/">
    AWS Security Blog
  </a>
</p>

<p align="center">
  <strong>Community Post:</strong>
  <a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2187144322050528">
    AWS Study Group – Facebook
  </a>
</p>