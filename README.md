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

The group policy defines the permissions granted to the `S3-Support` group.

![S3-Support Group Policy](03-desc_premession%20group%20S3_Support.png)

#### Access Test

`user-1` was tested to verify the permissions granted by the `S3-Support` group.

![user-1 S3 Access](04-user%201%20allow%20s3.png)

The user was denied access to Amazon EC2 because no EC2 permissions were assigned.

![user-1 EC2 Access Denied](05-user%201%20deny%20ec2.png)

![user-1 EC2 Access Denied](06-user1%20deny%20ec2.png)

The user was able to read the assigned S3 bucket.

![user-1 Read S3 Bucket](07-user1%20allow%20read%20bucket.png)


### 3. user-2 – EC2 Support

`user-2` is a member of the `EC2-Support` group and has permissions to view Amazon EC2 resources.

![user-2 in EC2-Support Group](08-user2%20in%20group%20EC2_Support.png)

The `EC2-Support` group has permissions assigned to support Amazon EC2 resources.

![EC2-Support Group Permissions](09-premession%20group%20EC2_Support.png)

The group policy defines the permissions granted to the `EC2-Support` group.

![EC2-Support Group Policy](10-desc_premession%20group%20EC2_Support.png)

#### Access Test

`user-2` was tested to verify the assigned EC2 permissions.

![user-2 EC2 Access](11-user%202%20allow%20ec2.png)

The user was able to view EC2 resources.

![user-2 View EC2](12-user%202%20allow%20see%20ec2.png)

The user was denied permission to stop an EC2 instance.

![user-2 Stop EC2 Denied](13-user%202%20deny%20stop%20ec2.png)

The user was denied access to Amazon S3.

![user-2 S3 Access Denied](14-user%202%20deny%20s3.png)


### 4. user-3 – EC2 Admin

`user-3` is a member of the `EC2-Admin` group and has permissions to manage Amazon EC2 resources.

![user-3 in EC2-Admin Group](15-user%203%20in%20group%20EC2_Admin.png)
The `EC2-Admin` group has permissions to manage Amazon EC2 resources.

![EC2-Admin Group Permissions](16-premession%20group%20EC2_Admin.png)

The group policy defines the permissions granted to the `EC2-Admin` group.

![EC2-Admin Group Policy](17-desc_premession%20group%20EC2_Admin.png)

#### Access Test

`user-3` was tested to verify the assigned EC2 permissions.

![user-3 Stop EC2 Permission](18-user%203%20allow%20stop%20ec2.png)

The user was able to stop an EC2 instance successfully.

![user-3 Stop EC2](19-user%203%20stop%20ec2.png)
