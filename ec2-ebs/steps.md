# 🚀 AWS CLI Setup & IAM User Configuration

## 📌 Overview
This guide explains how to:  
- Install **AWS CLI on Ubuntu**  
- Create an **IAM user with CLI-only access**  
- Generate **Access Keys**  
- Configure AWS CLI  
- Verify setup using EC2 commands  

---

## 🪜 Steps Performed

### 1️⃣ Install AWS CLI on Ubuntu
Ran the following commands:

```bash
sudo snap install aws-cli --classic
aws --version
sudo apt update
sudo apt install unzip -y
unzip awscliv2.zip
sudo ./aws/install
```

### 2️⃣ Open AWS Console & Search IAM
- Logged in to **AWS Console**  
- Searched for **IAM** service  

📸 ![Step 2: Search IAM](screenshot/search.png)

---

### 3️⃣ IAM Dashboard → Users
- Opened **IAM Dashboard**  
- Navigated to **Users** section  

📸 ![Step 3: IAM Dashboard](screenshot/Dashboard.png)

- Check User List
  
📸 ![Step 3a: User list](screenshot/userlist.png)

---

### 4️⃣ Create New IAM User
- Clicked **Add User**  
- Entered username
  
📸 ![Step 4: Create User](screenshot/username.png)
   
- Unticked **Provide AWS Management Console access**
- Selected **Attach policies directly** and assigned permissions  

📸 ![Step 4: Create User](screenshot/permissions.png)

---

### 5️⃣ Review & Create User
- Reviewed configuration  
- Created IAM user successfully ✅  

📸 ![Step 5: Review](screenshot/review.png)

- Confirm User are created or Not

📸 ![Step 5: Review](screenshot/confirmuser.png)

---

### 6️⃣ Generate Access Key
- Went to **Security Credentials**
  
📸 ![Step 6: Access Key](screenshot/view-user.png)
 
- Created new **Access Key** (for CLI)

📸 ![Step 6: Access Key](screenshot/access-key.png)
   
- Added description, confirmed, and downloaded `.csv`  

📸 ![Step 6b: Access Key Review](screenshot/RW-AC.png)

---

### 7️⃣ Configure AWS CLI on Ubuntu
Configured AWS CLI with keys and region:

📸 ![Step 7: Ubuntu Confirmation](screenshot/ubuntu.png)

---

### 8️⃣ Verify Setup

Checked EC2 instances via CLI:

aws ec2 describe-instances

---

🎯 Final Outcome

✅ AWS CLI installed on Ubuntu

✅ IAM user created with CLI-only access

✅ Access Key configured

✅ Verified AWS CLI with EC2 command
AWS Secret Access Key
Default region: ap-south-1
Default output format: json
