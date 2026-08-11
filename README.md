# AWS IAM Permissions Lab – S3 and EC2

## Project Overview

This hands-on lab demonstrates how AWS IAM permissions control access to Amazon S3 and Amazon EC2 resources.

## Objectives

- Understand AWS IAM users and groups.
- Explore IAM permissions and policies.
- Test access to Amazon S3 resources.
- Test access to Amazon EC2 resources.
- Understand how permissions determine what an IAM user can access.

## Lab Environment

- AWS Management Console
- AWS Identity and Access Management (IAM)
- Amazon S3
- Amazon EC2

## IAM Users and Groups

### user-1

- IAM Group: S3-Support
- Access: Amazon S3
- Amazon EC2: No access

### user-2

- IAM Group: EC2-Support
- Access: Amazon EC2
- Permission: Can view EC2 resources but cannot stop instances
- S3: No access

### user-3

- IAM Group: EC2-Admin
- Access: Amazon EC2
- Permission: Can view and stop EC2 instances
- S3: No access
  
## Lab Steps

### 1. IAM User and Group Configuration

The lab uses three IAM users with different groups and permissions:

- `user-1` → `S3-Support`
- `user-2` → `EC2-Support`
- `user-3` → `EC2-Admin`
### 2. user-1 – S3 Support

`user-1` is a member of the `S3-Support` group and has permissions to access Amazon S3 resources.
![user-1 in S3-Support Group](01-user%201%20in%20gruop%20S3_Support.png)

The `S3-Support` group has permissions that allow `user-1` to access Amazon S3 resources.
![S3-Support Group Permissions](02-premession%20group%20S3_Support.png)
