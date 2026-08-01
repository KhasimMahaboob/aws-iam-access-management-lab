# AWS IAM Access Management Lab

## Project Overview

This repository documents my hands-on learning of **AWS Identity and Access Management (IAM)** by implementing real-world access control scenarios following the **Principle of Least Privilege**.

The project demonstrates how different AWS IAM components work together to securely manage access to AWS resources through practical labs.

Throughout this project I implemented:

- IAM Users
- IAM Groups
- AWS Managed Policies
- Customer Managed Policies
- Inline Policies
- IAM Policy Simulator
- IAM Roles
- AWS STS (Security Token Service)
- EC2 Instance Profiles
- Secure EC2 → Amazon S3 Authentication

---

# Technologies Used

- Amazon Web Services (AWS)
- AWS IAM
- Amazon EC2
- Amazon S3
- AWS STS
- AWS CLI
- Ubuntu EC2 Instance

---

# Lab 1 – IAM Users & Groups

## Objective

Create multiple IAM users and organize them using IAM Groups.

### IAM Users

- CloudAdmin
- Developer1
- Developer2
- Intern1

### IAM Groups

- Administrators
- Developers
- Interns
  ## Screenshots
  ![IAM Users](IAM Users.png)
---

# Lab 2 – AWS Managed Policies

AWS Managed Policies attached:

- AdministratorAccess
- ReadOnlyAccess

These policies were assigned through IAM Groups to simplify permission management.

---

# Lab 3 – Customer Managed Policies

## DeveloperEC2StartStopPolicy

### Allowed

- ec2:DescribeInstances
- ec2:StartInstances
- ec2:StopInstances

### Restricted

- Launch EC2 Instances
- Terminate EC2 Instances

---

## DeveloperS3AccessPolicy

### Allowed

- List Buckets
- Upload Objects
- Download Objects

### Restricted

- Delete Objects
- Delete Buckets

---

# Lab 4 – Inline Policy

Developer1 received an additional Inline Policy allowing:

- ec2:RebootInstances

Developer2 intentionally did **not** receive this permission.

This demonstrates how Inline Policies can provide user-specific permissions.

---

# Lab 5 – IAM Policy Simulator

IAM Policy Simulator was used to verify permissions for each IAM user.

Verified scenarios included:

- CloudAdmin → Full administrative access
- Developer1 → Start, Stop and Reboot EC2
- Developer2 → Start and Stop EC2 only
- Intern1 → Read-only access

This helped validate permission evaluation before testing with actual AWS resources.

---

# Lab 6 – IAM Roles (EC2 → Amazon S3)

## Objective

Provide secure access from an Amazon EC2 instance to Amazon S3 **without storing AWS Access Keys or Secret Keys**.

## Steps Performed

- Created IAM Role: **EC2-S3-Access-Role**
- Selected EC2 as Trusted Entity
- Attached AmazonS3FullAccess policy
- Attached IAM Role to an existing EC2 instance
- Launched another EC2 instance with the IAM Role attached during creation
- Installed AWS CLI
- Verified temporary credentials using AWS STS
- Successfully accessed Amazon S3 without configuring access keys

---

## Verification

Verified IAM Role using:

```bash
aws sts get-caller-identity
```

Result:

- Temporary credentials generated through AWS STS
- EC2 successfully assumed EC2-S3-Access-Role

Verified S3 access using:

```bash
aws s3 ls
```

Successfully listed S3 buckets without using long-term credentials.

---

# Permission Testing

## CloudAdmin

✅ Full Administrative Access

---

## Developer1

### Allowed

- Start EC2
- Stop EC2
- Reboot EC2
- Upload S3 Objects
- Download S3 Objects

### Denied

- Launch EC2
- Terminate EC2
- Delete S3 Objects
- IAM Administration

---

## Developer2

### Allowed

- Start EC2
- Stop EC2
- Upload Objects
- Download Objects

### Denied

- Reboot EC2
- Launch EC2
- Terminate EC2

---

## Intern1

### Allowed

- Read-only access

### Denied

- Launch EC2
- Modify Resources
- Create S3 Buckets

---

# Key Concepts Learned

- IAM Users
- IAM Groups
- AWS Managed Policies
- Customer Managed Policies
- Inline Policies
- IAM Roles
- Trust Relationships
- AWS STS
- Temporary Security Credentials
- EC2 Instance Profiles
- IAM Policy Simulator
- Identity-Based Policies
- Principle of Least Privilege
- Role-Based Access Control (RBAC)
- AWS Security Best Practices

---

# Repository Structure

```
aws-iam-access-management-lab/
│
├── Screenshots/
└── README.md
```

---

# Author

**Shaik Khasim Mahaboob**

Learning AWS Cloud Computing through hands-on projects while building practical cloud security and IAM implementations.
