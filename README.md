# AWS IAM Permissions Lab – S3 and EC2

## Project Overview

This hands-on lab demonstrates how AWS IAM users, groups, and permissions control access to Amazon S3 and Amazon EC2 resources.

The lab includes three IAM users with different levels of access. Each user's permissions were tested to verify what they can and cannot do.

## Objectives

* Understand AWS IAM users and groups.
* Explore IAM permissions and policies.
* Understand how IAM permissions control access to AWS resources.
* Test access to Amazon S3 resources.
* Test access to Amazon EC2 resources.
* Verify allowed and denied actions for different IAM users.

## Lab Environment

* AWS Management Console
* AWS Identity and Access Management (IAM)
* Amazon S3
* Amazon EC2

## IAM Users and Groups

| User     | IAM Group     | Access     | Permissions                                                     |
| -------- | ------------- | ---------- | --------------------------------------------------------------- |
| `user-1` | `S3-Support`  | Amazon S3  | Can access S3 resources. No EC2 access.                         |
| `user-2` | `EC2-Support` | Amazon EC2 | Can view EC2 resources but cannot stop instances. No S3 access. |
| `user-3` | `EC2-Admin`   | Amazon EC2 | Can view and stop EC2 instances. No S3 access.                  |

---

## Lab Steps

### 1. IAM User and Group Configuration

The lab uses three IAM users with different groups and permissions:

* `user-1` → `S3-Support`
* `user-2` → `EC2-Support`
* `user-3` → `EC2-Admin`

  ### 2. user-1 – S3 Support

`user-1` is a member of the `S3-Support` group and has permissions to access Amazon S3 resources.

![user-1 in S3-Support Group](01-user%201%20in%20gruop%20S3_Support.png)

The `S3-Support` group permissions:

![S3-Support Group Permissions](02-premession%20group%20S3_Support.png)

The group policy:

![S3-Support Group Policy](03-desc_premession%20group%20S3_Support.png)

#### Access Tests

`user-1` can access Amazon S3:

![user-1 S3 Access](04-user%201%20allow%20s3.png)

`user-1` is denied access to Amazon EC2:

![user-1 EC2 Access Denied](05-user%201%20deny%20ec2.png)

![user-1 EC2 Access Denied](06-user1%20deny%20ec2.png)

`user-1` can read the S3 bucket:

![user-1 Read S3 Bucket](07-user1%20allow%20read%20bucket.png)

---

### 3. user-2 – EC2 Support

`user-2` is a member of the `EC2-Support` group.

![user-2 in EC2-Support Group](08-user2%20in%20group%20EC2_Support.png)

The `EC2-Support` group permissions:

![EC2-Support Group Permissions](09-premession%20group%20EC2_Support.png)

The group policy:

![EC2-Support Group Policy](10-desc_premession%20group%20EC2_Support.png)

#### Access Tests

`user-2` can access Amazon EC2:

![user-2 EC2 Access](11-user%202%20allow%20ec2.png)

`user-2` can view EC2 instances:

![user-2 View EC2](12-user%202%20allow%20see%20ec2.png)

`user-2` cannot stop EC2 instances:

![user-2 Stop EC2 Denied](13-user%202%20deny%20stop%20ec2.png)

`user-2` is denied access to Amazon S3:

![user-2 S3 Access Denied](14-user%202%20deny%20s3.png)

---

### 4. user-3 – EC2 Admin

`user-3` is a member of the `EC2-Admin` group and has permissions to manage Amazon EC2 resources.

![user-3 in EC2-Admin Group](15-user%203%20in%20gruop%20EC2_Admin.png)

The `EC2-Admin` group permissions:

![EC2-Admin Group Permissions](16-premession%20group%20EC2_Admin.png)

The group policy:

![EC2-Admin Group Policy](17-desc_premession%20group%20EC2_Admin.png)

#### Access Test

`user-3` is allowed to stop EC2 instances:

![user-3 Allow Stop EC2](18-user%203%20allow%20stop%20ec2.png)

The EC2 instance was successfully stopped:

![user-3 Stop EC2](19-user%203%20stop%20ec2.png)




