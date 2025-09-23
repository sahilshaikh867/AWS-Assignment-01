# Task 1: AWS IAM

## Overview
IAM (Identity and Access Management) allows you to control **who can access your AWS account** and **what actions they can perform**.  

This task covers:  
- Searching IAM service  
- Viewing dashboard  
- Managing users  
- Creating new users with permissions  
- Enabling console access and MFA  

---

## Step 1: Search IAM Service
- Go to AWS Console  
- In the search bar, type **IAM** and select the service  

![Step 1: Search IAM](screenshots/step1-search-iam.png)

---

## Step 2: IAM Dashboard
- View the IAM dashboard  

![Step 2: Dashboard](screenshots/step2-dashboard.png)

---

## Step 3: Users List
- Go to **Users** section to see existing IAM users  

![Step 3: Users List](screenshots/step3-users-list.png)

---

## Step 4: Create New User
1. Click **Add user**  
2. Specify username and access type (Programmatic / Console)  

![Step 4: Specify User Details](screenshots/step4-user-details.png)

---

## Step 5: Set Permissions
- Attach existing policies or add to a group  
- Choose required permissions for the user  

![Step 5: Set Permissions](screenshots/step5-set-permissions.png)

---

## Step 6: Review User
- Review all settings before creating the user  
- Confirm and create user  

![Step 6: Review User](screenshots/step6-review.png)

---

## Step 7: Verify User in List
- Check the newly created user in **Users list**  

![Step 7: User List](screenshots/step7-user-list.png)

---

## Step 8: Security Credentials
1. Select user  
2. Go to **Security credentials** tab  
3. View user info, enable console access, and configure MFA  

![Step 8: Security Credentials](screenshots/step8-security-credentials.png)  
![Step 8a: User Info](screenshots/step8a-user-info.png)  
![Step 8b: Enable Console Access](screenshots/step8b-console-access.png)  
![Step 8c: MFA Access](screenshots/step8c-mfa.png)

---

## Notes
- Keep Access Key and Secret Key secure  
- Enable MFA for extra security  
- Follow least privilege principle when assigning permissions
