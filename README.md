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

| User     | IAM Group     | Access     | Permissions                                                          |
| -------- | ------------- | ---------- | -------------------------------------------------------------------- |
| `user-1` | `S3-Support`  | Amazon S3  | Read-Only access to Amazon S3. No EC2 access.                        |
| `user-2` | `EC2-Support` | Amazon EC2 | Read-Only access to Amazon EC2. Cannot stop instances. No S3 access. |
| `user-3` | `EC2-Admin`   | Amazon EC2 | Can view, start, and stop EC2 instances. No S3 access.               |

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



### Group Permissions

The `S3-Support` group provides Read-Only access to Amazon S3.



### Permission Policy

The policy defines the permissions assigned to the `S3-Support` group.



### Access Tests

`user-1` was able to access Amazon S3 resources.



`user-1` was denied access to Amazon EC2.



`user-1` was also denied access to Amazon EC2 resources.



`user-1` was able to read the S3 bucket.



### Result

- S3 access: **Allowed (Read-Only)**
- EC2 access: **Denied**

---

## 3. user-2 – EC2 Support

`user-2` is a member of the `EC2-Support` group and has Read-Only access to Amazon EC2 resources.

### Group Membership



### Group Permissions

The `EC2-Support` group provides Read-Only access to Amazon EC2.



### Permission Policy

The policy allows `user-2` to view Amazon EC2 resources but does not allow stopping instances.



### Access Tests

`user-2` was able to access Amazon EC2 resources.



`user-2` was able to view EC2 instances.



`user-2` was denied permission to stop an EC2 instance.



`user-2` was denied access to Amazon S3.



### Result

- EC2 read/view access: **Allowed**
- EC2 stop instance: **Denied**
- S3 access: **Denied**

---

## 4. user-3 – EC2 Admin

`user-3` is a member of the `EC2-Admin` group and has permissions to manage Amazon EC2 instances.

The `EC2-Admin` permissions allow the user to:

- View EC2 instances
- Start EC2 instances
- Stop EC2 instances

### Group Membership



### Group Permissions

The `EC2-Admin` group provides permissions to manage Amazon EC2 instances.



### Permission Policy

The policy allows the user to view, start, and stop EC2 instances.



### Access Test

`user-3` was allowed to stop an EC2 instance.



The EC2 instance was successfully stopped.



### Result

- EC2 view access: **Allowed**
- EC2 start instance: **Allowed by policy**
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
- Can start EC2 instances.
- Can stop EC2 instances.
- Cannot access Amazon S3.

---

# Key Takeaways

- IAM users can be assigned to IAM groups.
- IAM groups can have policies attached to them.
- IAM policies define which actions users are allowed or denied to perform.
- Different users can have different levels of access to AWS resources.
- Testing both allowed and denied actions helps verify that IAM permissions are configured correctly.
- IAM permissions should follow the principle of least privilege.
