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

![Step 1: Search IAM](iam-screenshots/first.png)

---

## Step 2: IAM Dashboard
- View the IAM dashboard  

![Step 2: Dashboard](iam-screenshots/ss1.png)

---

## Step 3: Users List
- Go to **Users** section to see existing IAM users  

![Step 3: Users List](aim-screenshots/users.png)

---

## Step 4: Create New User
1. Click **Add user**  
2. Specify username and access type (Programmatic / Console)  

![Step 4: Specify User Details](iam-screenshots/ss3.png)

---

## Step 5: Set Permissions
- Attach existing policies or add to a group  
- Choose required permissions for the user  

![Step 5: Set Permissions](aim-screenshots/ss3.png)

---

## Step 6: Review User
- Review all settings before creating the user  
- Confirm and create user  

![Step 6: Review User](iam-screenshots/ss5.png)

---

## Step 7: Verify User in List
- Check the newly created user in **Users list**  

![Step 7: User List](iam-screenshots/ss6.png)

---

## Step 8: Security Credentials
1. Select user  
2. Go to **Security credentials** tab  
3. View user info, enable console access, and configure MFA  

![Step 8: Security Credentials](iam-screenshots/ss7.png)  
![Step 8a: User Info](iam-screenshots/ss8.png)  
![Step 8b: Enable Console Access](iam-screenshots/ss9.png)  
![Step 8c: MFA Access](iam-screenshots/ss10.png)
![Step 8d: MFA Access](iam-screenshots/ss11.png)
---

## Notes
- Keep Access Key and Secret Key secure  
- Enable MFA for extra security  
- Follow least privilege principle when assigning permissions
