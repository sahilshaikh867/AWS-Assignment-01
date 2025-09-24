# 💾 Task: Take EBS Snapshot & Restore New Volume

## 📌 Overview
This guide walks through:  
- Taking a **snapshot** of an existing EBS volume  
- Restoring a **new volume** from that snapshot  
- Attaching and mounting the restored volume to an EC2 instance  

> ⚠️ **Security Note:** Never include real AWS credentials in public repositories. Always use placeholders.

---

## 🪜 Step-by-Step Guide

### 1️⃣ Select EC2 Instance
- Navigate to **EC2 Console → Instances**  
- Identify the instance whose volume you want to snapshot  

📸 ![Step 1: Select Instance](screenshots/cmd1.png)

---

### 2️⃣ Identify EBS Volume
- Go to **Volumes → Select the attached volume**  
- Note **Volume ID** and **Availability Zone**  

📸 ![Step 2: Select Volume](screenshots/cmd2.png)

---

### 3️⃣ Create Snapshot
- Click **Actions → Create Snapshot**  
- Provide a **name** and optional **description**  
- Click **Create Snapshot** ✅  

📸 ![Step 3: Create Snapshot](screenshots/cmd3.png)

> ⏳ Snapshot creation may take a few minutes depending on the volume size.

---

### 4️⃣ Verify Snapshot
- Navigate to **Snapshots**  
- Ensure snapshot status is **Completed**  

📸 ![Step 4: Snapshot Completed](screenshots/cmd4.png)

---

### 5️⃣ Restore New Volume from Snapshot
- Select snapshot → **Actions → Create Volume**  
- Configure **size, type, Availability Zone**  
- Click **Create Volume**  

📸 ![Step 5: Create Volume](screenshots/cmd5.png)

---

### 6️⃣ Attach New Volume to EC2
- Go to **Volumes → Select new volume → Actions → Attach Volume**  
- Choose **Target EC2 Instance** and **Device Name** (e.g., `/dev/sdf`)  

📸 ![Step 6: Attach Volume](screenshots/cmd6.png)

---

### 7️⃣ Mount the Volume on EC2
```bash
sudo mkdir -p /mnt/ebs
sudo mount /dev/nvme1n1 /mnt/ebs
ls /mnt/ebs
