# AWS IAM Task - Task 1

## Overview
This task covers the essentials of **AWS Identity and Access Management (IAM)**.  
IAM lets you **control who can access your AWS account** and **what they can do**.  

In this task, we:  
- Created a new IAM user with proper permissions  
- Explored the IAM dashboard and users list  
- Configured console access and programmatic access  
- Enabled **Multi-Factor Authentication (MFA)** for extra security  

---

## Task Steps & Highlights

### 1️⃣ Search & Access IAM
- Open AWS Management Console  
- Search for **IAM** in the services search bar  
- Accessed the IAM dashboard  

*This is where you get an overview of all IAM resources: users, groups, roles, and policies.*

---

### 2️⃣ Users Management
- Checked existing IAM users  
- Reviewed permissions and user activity  
- Understood user info and security credentials  

*Knowing your users is the first step in managing access effectively.*

---

### 3️⃣ Create a New User
- Clicked **Add User**  
- Specified **username** and **access type** (CLI/programmatic or console)  
- Set permissions based on task requirements  

*Best practice: Start with minimal permissions and expand as needed.*

---

### 4️⃣ Review & Verify
- Reviewed user details  
- Confirmed settings and created the user  
- Verified the new user appears in the **users list**  

*Always double-check before creating users to avoid permission mistakes.*

---

### 5️⃣ Security & MFA
- Went to **Security Credentials** for the user  
- Enabled **Console Access** and **MFA**  
- Ensured the user account has **enhanced security**  

*MFA adds an extra layer of protection in case credentials are compromised.*

---

## Key Takeaways
- IAM is the backbone of AWS security  
- Always use the **least privilege principle**  
- Enabling **MFA** is a must for sensitive accounts  
- Proper user management prevents unauthorized access and keeps your AWS environment safe  

---

💡 **Pro Tip:**  
For documentation, always maintain a **screenshots folder** in the IAM repo to visually track each step.  
You can link images in Markdown like:

```markdown
![Create User Screenshot](iam-screenshots/create-user.png)
