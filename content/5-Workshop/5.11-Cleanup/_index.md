---
title : "Cleanup"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b>5.11. </b> "
---

After completing the entire workshop and confirming that the system is operating as expected, the final step is **Cleanup**. The purpose of this step is to remove the AWS resources created during the workshop to avoid unnecessary charges.

Cleaning up unused resources also helps keep your AWS environment organized and ready for future deployments.

---

## Objectives

After completing this section, you will be able to:

- Remove AWS resources that are no longer needed.
- Minimize unnecessary AWS costs after completing the workshop.
- Ensure that the AWS environment is completely cleaned up.
- Prepare your AWS account for future projects or workshops.

---

## Resources to Review

During the cleanup process, review and remove the resources created throughout the workshop, including:

- Amazon EC2 Instances.
- Auto Scaling Group.
- Application Load Balancer.
- Target Group.
- Launch Template.
- Amazon S3 Buckets (if no longer required).
- Amazon CloudWatch Alarms.
- Amazon API Gateway.
- AWS Lambda Functions.
- Amazon Location Service resources.
- IAM Roles or Policies created specifically for the workshop (if no longer needed).

---

## Cleanup Procedure

Perform the following steps:

1. Stop or terminate the Amazon EC2 instances.
2. Delete the Auto Scaling Group.
3. Delete the Application Load Balancer.
4. Delete the Target Group.
5. Delete the Launch Template.
6. Remove any additional AWS resources created during the workshop that are no longer required.
7. Review your AWS account to ensure that no billable resources remain.

---

## Notes

Before deleting any resources, make sure that:

- There is no important data that still needs to be retained.
- No services are currently using these resources.
- Any important data has been backed up if necessary.

The cleanup process should be performed only after all testing has been completed and the system has been confirmed to be operating correctly.

---

## Results

After completing the cleanup process:

- All unused AWS resources have been removed.
- The AWS account is clean and well organized.
- No unnecessary AWS charges will be incurred.
- The workshop has been completed successfully, and the environment is ready for future deployments.