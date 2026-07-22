---
title : "End-to-End Testing"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b>5.10. </b> "
---

After completing all the previous labs, the final step is to perform **End-to-End Testing** to verify that the entire system is functioning correctly.

This testing process ensures that all AWS services have been deployed and configured properly, and that the application operates reliably from end to end.

---

## Objectives

After completing this section, you will be able to:

- Verify the connectivity between AWS services.
- Confirm that the Application Load Balancer is functioning correctly.
- Verify the Auto Scaling Group and the Amazon EC2 instances.
- Test application access from the Internet.
- Ensure that the entire system operates reliably.

---

## Testing Architecture

```text
User
   │
   ▼
Application Load Balancer
   │
   ▼
Target Group
   │
   ▼
Amazon EC2 Instances
   │
   ▼
Application
```

The user sends requests to the **Application Load Balancer**, which forwards the requests to the Amazon EC2 instances registered in the **Target Group** for processing.

---

## Testing Activities

The following tasks are performed in this section:

- Verify the Application Load Balancer.
- Verify the Target Group health checks.
- Verify the Auto Scaling Group.
- Access the application through the Load Balancer DNS name.
- Confirm that the application is functioning correctly.

---

## Success Criteria

The deployment is considered successful when:

- The Application Load Balancer status is **Active**.
- The Target Group reports all EC2 instances as **Healthy**.
- The Auto Scaling Group operates normally.
- The application is accessible through the Load Balancer DNS name.
- No errors occur during the testing process.

---

## Results

After completing the End-to-End Testing:

- All AWS services have been successfully integrated.
- The application is operating reliably.
- The system meets the requirements for scalability and high availability.
- The workshop has been completed successfully.