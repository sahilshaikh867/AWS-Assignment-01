# 📊 AWS CloudWatch & Auto Scaling Group (ASG) Setup

## 📌 Overview

This guide demonstrates how to:  

- Monitor **EC2 instances** with CloudWatch  
- Set up **CPU utilization alarms**  
- Integrate CloudWatch alarms with **Auto Scaling Groups (ASG)**  
- Automatically **scale instances** based on demand  

> ⚠️ **Security Reminder:** Do **not** include any AWS credentials in public repositories. Always use placeholders.

---

## 🪜 Step-by-Step Implementation

### 1️⃣ Set Up CloudWatch Alarm

1. Navigate to **AWS Console → CloudWatch → Alarms → Create Alarm**  
2. Select the EC2 instance and choose **CPUUtilization** as the metric  
3. Set threshold: **≥ 50%**  
4. Configure **actions**: send notification via SNS or trigger Auto Scaling policies  

📸 ![Step 1: CloudWatch Alarm](screenshots/cw1.png)

💡 **Tip:** Always provide a clear name for the alarm for easy identification.

---

### 2️⃣ Create Auto Scaling Group (ASG)

1. Navigate to **EC2 → Auto Scaling Groups → Create Auto Scaling Group**  
2. Choose **Launch Template** or **AMI**  
3. Configure **minimum, desired, and maximum instance count**  
4. Attach **CloudWatch alarm** to trigger scale in/out actions  
5. Review and **create ASG**  

📸 ![Step 2: ASG Setup](screenshots/cw2.png)  
📸 ![Step 2a: ASG Configuration](screenshots/cw2a.png)

💡 **Tip:** Define scaling policies based on CPU or other metrics to efficiently manage load.

---

### 3️⃣ Test and Verify

1. Simulate **high CPU usage** to test the alarm  
2. Check if **CloudWatch Alarm triggers** and ASG responds by launching new instances  
3. Monitor **EC2 instances and metrics** to ensure scaling is working correctly  

📸 ![Step 3: Verify ASG Response](screenshots/cw3.png)  
📸 ![Step 3a: CloudWatch Metrics](screenshots/cw3a.png)

---

## 🎯 Expected Outcome

- ✅ CloudWatch alarm triggers when CPU exceeds threshold  
- ✅ Auto Scaling Group launches or terminates instances automatically  
- ✅ EC2 instances scale based on actual load  
- ✅ Monitoring & automation reduces manual intervention  

---

## 📂 Repository Structure Suggestion
