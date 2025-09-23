# 🖥️ Task 2: Create AMI from EC2 Instance & Launch Another Instance

## 📌 Overview
This guide walks you through the process of:  

- Creating an **Amazon Machine Image (AMI)** from an existing EC2 instance  
- Launching a **new EC2 instance** using the created AMI  

> ⚠️ **Security Note:** Do **not** include any real AWS credentials in public repositories. Always use secure placeholders.

---

## 🪜 Step-by-Step Guide

### 1️⃣ Select Existing EC2 Instance
- Navigate to **EC2 Console → Instances**  
- Select the instance you want to use for creating an AMI  

📸 ![Step 1: Select Instance](screenshots/step1-select-instance.png)

---

### 2️⃣ Create Image (AMI)
- Click **Actions → Image → Create Image**  
- Enter a **descriptive name** and optional **description**  
- Configure **volumes** and other settings if needed  
- Click **Create Image** ✅  

📸 ![Step 2: Create Image](screenshots/step2-create-image.png)

> 💡 **Tip:** Include a clear description to identify the AMI later.

---

### 3️⃣ Verify AMI Creation
- Go to **AMIs** section in EC2 Console  
- Wait for the AMI status to show **Available**  

📸 ![Step 3: AMI Available](screenshots/step3-ami-available.png)

> ⏳ **Note:** Depending on instance size, AMI creation may take a few minutes.

---

### 4️⃣ Launch New EC2 Instance
- Select the newly created AMI  
- Click **Launch Instance**  
- Choose **Instance Type**, configure **Network & Security Group**  
- Review settings and **launch** the instance  
- Verify that the instance is **running and accessible**  

📸 ![Step 4: Launch Instance](screenshots/step4-launch-instance.png)

> ⚠️ **Reminder:** Ensure you are in the **correct region** when launching the new instance.

---

## 🎯 Outcome
- ✅ Successfully created an **AMI** from an existing EC2 instance  
- ✅ Launched a **new EC2 instance** from the AMI  
- ✅ Verified the instance is running and accessible  

---

## 📂 Repository Structure Suggestion

