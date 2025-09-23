# 💾 Task 4: Create & Mount EBS Volume to EC2 Instance

## 📌 Overview
This guide explains how to:  
- Create a new **EBS Volume** in AWS  
- Attach it to an **existing EC2 instance**  
- Mount and format the volume inside the instance  

> ⚠️ **Security Note:** Always ensure the EBS volume is in the **same Availability Zone (AZ)** as your EC2 instance.

---

## 🪜 Step-by-Step Guide

### 1️⃣ Create a New EBS Volume
- Go to **EC2 Console → Elastic Block Store → Volumes**  
- Click **Create Volume**  
- Choose:  
  - **Volume type:** gp2 (General Purpose SSD)  
  - **Size:** as per requirement (e.g., 5 GiB)  
  - **Availability Zone (AZ):** same as your EC2 instance  
- Click **Create Volume** ✅  

📸 ![Step 1: Create Volume](screenshots/step1-create-volume.png)

---

### 2️⃣ Attach Volume to EC2 Instance
- Select the newly created volume  
- Click **Actions → Attach Volume**  
- Choose the target **EC2 instance**  
- Note the **device name** (e.g., `/dev/sdf`)  

📸 ![Step 2: Attach Volume](screenshots/step2-attach-volume.png)

---

### 3️⃣ Verify Volume in EC2 Instance
- Connect to your EC2 instance via SSH  
- Run the following command to list block devices:  

```bash
lsblk
