# AWS IAM Permissions Lab – S3 and EC2

## Project Overview

This hands-on lab demonstrates how AWS IAM users, groups, and permissions control access to Amazon S3 and Amazon EC2 resources.

The lab includes three IAM users with different levels of access. Each user's permissions were tested to verify what they can and cannot do.

## Objectives

- Understand AWS IAM users and groups.
- Explore IAM permissions and policies.
- Understand how IAM permissions control access to AWS resources.
- Test access to Amazon S3 resources.
- Test access to Amazon EC2 resources.
- Verify allowed and denied actions for different IAM users.

## Lab Environment

- AWS Management Console
- AWS Identity and Access Management (IAM)
- Amazon S3
- Amazon EC2

---

## IAM Users and Groups

| User | IAM Group | Access | Permissions |
|---|---|---|---|
| `user-1` | `S3-Support` | Amazon S3 | Read-Only access to Amazon S3. No EC2 access. |
| `user-2` | `EC2-Support` | Amazon EC2 | Read-Only access to Amazon EC2. Cannot stop instances. No S3 access. |
| `user-3` | `EC2-Admin` | Amazon EC2 | Can view and stop EC2 instances. No S3 access. |

---

# Lab Steps

## 1. IAM User and Group Configuration

The lab uses three IAM users with different groups and permissions:

- `user-1` → `S3-Support`
- `user-2` → `EC2-Support`
- `user-3` → `EC2-Admin`

---

## 2. user-1 – S3 Support

`user-1` is a member of the `S3-Support` group and has Read-Only access to Amazon S3 resources.

### Group Membership

![User-1 in S3-Support Group](<01-user 1 in group S3_Support.png>)

### Group Permissions

The `S3-Support` group provides Read-Only access to Amazon S3.

![S3-Support Group Permissions](<02-pressemission group S3_Support.png>)

### Permission Policy

The policy defines the permissions assigned to the `S3-Support` group.

![S3-Support Permission Policy](<03-desc_premession group S3_Support.png>)

### Access Tests

`user-1` was able to access Amazon S3 resources.

![User-1 S3 Access](<04-user 1 allow s3.png>)

`user-1` was denied access to Amazon EC2.

![User-1 EC2 Access Denied](<05-user1 deny ec2.png>)

`user-1` was able to read the S3 bucket.

![User-1 Read S3 Bucket](<07-user1 allow read bucket.png>)

### Result

- S3 access: **Allowed (Read-Only)**
- EC2 access: **Denied**

---

## 3. user-2 – EC2 Support

`user-2` is a member of the `EC2-Support` group and has Read-Only access to Amazon EC2 resources.

### Group Membership

![User-2 in EC2-Support Group](<08-user-2 in EC2-Support Group.png>)

### Group Permissions

The `EC2-Support` group provides Read-Only access to Amazon EC2.

![EC2-Support Group Permissions](<09-premession group EC2_Support.png>)

### Permission Policy

The policy defines the permissions assigned to the `EC2-Support` group.

![EC2-Support Permission Policy](<10-desc_premession group EC2_Support.png>)

### Access Tests

`user-2` was able to access Amazon EC2 resources.

![User-2 EC2 Access](<11-user 2 allow ec2.png>)

`user-2` was able to view EC2 instances.

![User-2 View EC2](<12-user 2 allow see ec2.png>)

`user-2` was denied access to Amazon S3.

![User-2 S3 Access Denied](<14-user 2 deny s3.png>)

### Result

- EC2 read/view access: **Allowed**
- EC2 stop instance: **Denied**
- S3 access: **Denied**

---

## 4. user-3 – EC2 Admin

`user-3` is a member of the `EC2-Admin` group and has permissions to manage Amazon EC2 instances.

### Group Membership

![User-3 in EC2-Admin Group](<15-user 3 in group EC2_Admin.png>)

### Group Permissions

The `EC2-Admin` group provides permissions to manage Amazon EC2 instances.

![EC2-Admin Group Permissions](<16-pressemission group EC2_Admin.png>)

### Permission Policy

The policy defines the permissions assigned to the `EC2-Admin` group.

![EC2-Admin Permission Policy](<17-desc_premession group EC2_Admin.png>)

### Access Test

`user-3` was allowed to stop an EC2 instance.

![User-3 Stop EC2](<18-user 3 allow stop ec2.png>)

The EC2 instance was successfully stopped.

![User-3 EC2 Instance Stopped](<19-user 3 stop ec2.png>)

### Result

- EC2 view access: **Allowed**
- EC2 stop instance: **Allowed**
- S3 access: **Denied**

---

# Results

The lab successfully demonstrated how AWS IAM groups and policies control access to AWS resources.

### user-1 – S3 Support

- Can access Amazon S3.
- Has Read-Only S3 permissions.
- Cannot access Amazon EC2.

### user-2 – EC2 Support

- Can view Amazon EC2 resources.
- Cannot stop EC2 instances.
- Cannot access Amazon S3.

### user-3 – EC2 Admin

- Can view Amazon EC2 resources.
- Can stop EC2 instances.
- Cannot access Amazon S3.

---

# Key Takeaways

- IAM users can be assigned to IAM groups.
- IAM groups can have policies attached to them.
- IAM policies define which actions users are allowed or denied to perform.
- Different users can have different levels of access to AWS resources.
- Testing allowed and denied actions helps verify that IAM permissions are configured correctly.
- IAM permissions should follow the principle of least privilege.
