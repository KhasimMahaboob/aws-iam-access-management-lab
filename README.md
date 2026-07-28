# AWS IAM Access Management Lab

## Project Overview

This project demonstrates how AWS Identity and Access Management (IAM) is used to securely manage access to AWS resources by implementing the Principle of Least Privilege.

Instead of using the AWS Root Account for daily operations, IAM Users, User Groups, and AWS Managed Policies were configured to simulate a real-world organization's access control.

---

## Project Architecture

Root Account

├── Administrators Group

* AdministratorAccess

├── Developers Group

* AmazonEC2FullAccess
* AmazonS3FullAccess

└── Interns Group

* ReadOnlyAccess

IAM Users

* CloudAdmin → Administrators
* Developer1 → Developers
* Intern1 → Interns

---

## AWS Services Used

* AWS Identity and Access Management (IAM)
* Amazon EC2
* Amazon S3

---

## What I Implemented

### IAM Groups

* Administrators
* Developers
* Interns

### IAM Users

* CloudAdmin
* Developer1
* Intern1

### Policies Attached

Administrators

* AdministratorAccess

Developers

* AmazonEC2FullAccess
* AmazonS3FullAccess

Interns

* ReadOnlyAccess

---

## Permission Testing

### CloudAdmin

* Full administrative access
* Can manage IAM, EC2 and S3

### Developer1

* Can launch EC2 instances
* Can create S3 buckets
* Cannot manage IAM resources

### Intern1

* Can view AWS resources
* Cannot launch EC2 instances
* Cannot create Security Groups
* Cannot create S3 buckets

---

## Real Authorization Test

When logged in as **intern1**, attempting to launch an EC2 instance failed with the following error:

Action:
ec2:CreateSecurityGroup

Reason:
No identity-based policy allows the ec2:CreateSecurityGroup action.

This demonstrates how AWS evaluates IAM permissions for every API request before allowing an action.

---

## Key Concepts Learned

* IAM Users
* IAM Groups
* AWS Managed Policies
* Identity-Based Policies
* Permission Inheritance
* Principle of Least Privilege
* Role-Based Access Control (RBAC)
* Authorization Flow
* Access Denied Troubleshooting

---


---

## Skills Demonstrated

* AWS IAM
* Access Management
* AWS Security
* EC2 Permissions
* S3 Permissions
* Least Privilege Design
* Cloud Security Fundamentals

---

## Author

Shaik Khasim Mahaboob

Learning Cloud Computing through hands-on AWS projects.
