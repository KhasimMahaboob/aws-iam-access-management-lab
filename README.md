# AWS IAM Access Management Lab

## Project Overview

This project demonstrates hands-on implementation of **AWS Identity and Access Management (IAM)** by creating users, groups, managed policies, customer managed policies, and inline policies while following the Principle of Least Privilege.

The project simulates a real-world organization where different users have different levels of access based on their job responsibilities.

---

## Technologies Used

- Amazon Web Services (AWS)
- AWS IAM
- Amazon EC2
- Amazon S3

---

# IAM Users

- CloudAdmin
- Developer1
- Developer2
- Intern1

---

# IAM Groups

- Administrators
- Developers
- Interns

---

# AWS Managed Policies Used

- AdministratorAccess
- ReadOnlyAccess
- AmazonEC2FullAccess (initial setup)
- AmazonS3FullAccess (initial setup)

---

# Customer Managed Policies Created

## DeveloperEC2StartStopPolicy

Allowed:

- ec2:DescribeInstances
- ec2:StartInstances
- ec2:StopInstances

Restricted:

- Launch EC2 Instances
- Terminate EC2 Instances

---

## DeveloperS3AccessPolicy

Allowed:

- List Buckets
- Upload Objects
- Download Objects

Restricted:

- Delete Objects
- Delete Buckets

---

# Inline Policy

Developer1 received an additional inline policy allowing:

- ec2:RebootInstances

Developer2 did not receive this permission.

This demonstrates user-specific permission assignment using IAM Inline Policies.

---

# Permission Testing

## CloudAdmin

- Full AWS administrative access

## Developer1

Allowed:

- Start EC2
- Stop EC2
- Reboot EC2
- Upload objects to S3
- Download objects from S3

Denied:

- Launch EC2
- Terminate EC2
- Delete S3 Objects
- IAM Administration

## Developer2

Allowed:

- Start EC2
- Stop EC2

Denied:

- Reboot EC2
- Launch EC2
- Terminate EC2

## Intern1

Allowed:

- Read-only access

Denied:

- Launch EC2
- Create S3 Buckets
- Modify AWS Resources

---

# Key Concepts Learned

- IAM Users
- IAM Groups
- AWS Managed Policies
- Customer Managed Policies
- Inline Policies
- Principle of Least Privilege
- Role-Based Access Control (RBAC)
- Permission Evaluation
- AWS Security Best Practices

---

# Project Outcome

This lab demonstrates how IAM permissions can be designed, assigned, and verified using multiple AWS users while implementing secure access control following real-world cloud security practices.

---

## Repository Structure

```
aws-iam-access-management-lab
│
├── README.md
├── screenshots
└── policy-json
```

---

## Author

**Shaik Khasim Mahaboob**

Learning AWS Cloud Computing through hands-on projects.
