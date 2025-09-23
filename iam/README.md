# Task 1: AWS IAM

## Overview
IAM (Identity and Access Management) manages users, groups, roles, and permissions in AWS.

## Steps Completed

### 1. Create User
- Username: Sahil-devops
- Access Type: Programmatic & Console Access
- Permissions: Attached policy `AdministratorAccess`

![Create User Screenshot](screenshots/create-user.png)

### 2. Create Group
- Group Name: DevOps-Team
- Permissions: Attached policy `AdministratorAccess`
- Added user Sahil-devops to the group

![Create Group Screenshot](screenshots/create-group.png)

### 3. Create Role (Optional)
- Role Name: EC2-Access-Role
- Trusted entity: EC2
- Permissions: `AmazonS3FullAccess`

![Create Role Screenshot](screenshots/create-role.png)

### 4. Enable MFA
- Enabled MFA for user Sahil-devops using Google Authenticator

![Enable MFA Screenshot](screenshots/enable-mfa.png)

## Notes
- Keep Access Key & Secret Key secure.
- Start with simple permissions, then restrict based on least privilege principle.
