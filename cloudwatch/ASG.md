# 📊 AWS CloudWatch & Auto Scaling Group (ASG) Setup | Sahil Shaikh

Hi! I'm **Sahil Shaikh** 👋  
🔧 DevOps Engineer | Automation Enthusiast | Cloud & DevOps Lover  
💬 Fun Fact: I break things to automate them better 😎  

---

## 💡 Overview

In this guide, you will learn how to:

- Monitor **EC2 instance CPU usage** with CloudWatch  
- Set up **CPU utilization alarms**  
- Integrate alarms with **Auto Scaling Groups (ASG)**  
- Simulate high CPU load to test alarms and scaling  
- Verify scaling actions and CloudWatch metrics  

> ⚠️ **Security Reminder:** Never include AWS credentials in public repos. Always use placeholders.

---


## 🪜 Step-by-Step Guide

### 1️⃣ Prepare EC2 Instance

1. Launch an **EC2 instance** using Amazon Linux 2 AMI  
2. Make sure the instance has **security group** allowing SSH access  
3. Connect via SSH:  

```bash
ssh ec2-user@<instance-public-ip>
```
ssh ec2-user@<instance-public-ip>
Update system packages:

bash
Copy code
```
sudo yum update -y
```
---
### 2️⃣ Install Stress Tool

> Install stress to simulate CPU load:

Copy code
```
sudo yum install -y stress
```
---
> Verify installation:

Copy code 
```
stress --version
```
---

### 3️⃣ Create CloudWatch Alarm

> Navigate to AWS Console → CloudWatch → Alarms → Create Alarm

- Select EC2 instance → Metric: CPUUtilization

- Set threshold (e.g., ≥ 50%)

- Choose evaluation period (e.g., 1-5 minutes average)

- Configure actions:

"Trigger Auto Scaling policies"
---

 > Optional: send SNS notification

💡 Tip: Use a descriptive alarm name like HighCPU-EC2-1 for easy identification.
---
### 4️⃣ Create Auto Scaling Group (ASG)

> Navigate to EC2 → Auto Scaling Groups → Create ASG

> Choose Launch Template or AMI for instances
---
- Configure:

- Minimum instances: 1

- Desired instances: 1

- Maximum instances: 3 (adjust as needed)

- Attach CloudWatch alarm to trigger scale out/in policies
---
Review and create ASG

💡 Tip: Dynamic scaling policies ensure resources scale automatically with load.
---
### 5️⃣ Simulate CPU Load

> SSH into EC2 instance

- Run stress command:

Copy code
```
# Generate CPU load on 4 cores for 5 minutes
stress --cpu 4 --timeout 300
```
---
- While stress is running, monitor CloudWatch → Metrics → CPUUtilization

- Verify CPU spikes and check if CloudWatch alarm changes state
---
### 6️⃣ Verify Auto Scaling Actions

- Check EC2 → Auto Scaling Groups → Activity History

- Confirm that new instances launched automatically when CPU exceeded threshold

- Observe scale-in actions when CPU returns to normal

💡 Tip: Take note of instance IDs and timestamps to correlate with CloudWatch metrics.
---

### 7️⃣ Monitor Metrics

- Navigate to CloudWatch → Metrics → EC2

- Observe CPU utilization graphs

- Confirm alarms and scaling events are correctly recorded
---
### 8️⃣ Clean Up Resources

 > Terminate EC2 instances if no longer needed

 > Delete Auto Scaling Group

- Remove CloudWatch alarms

⚠️ Tip: Always clean up to avoid unnecessary AWS charges.
---

# 🎯 Expected Outcome

✅ CloudWatch alarm triggers when CPU exceeds threshold

✅ ASG launches/terminates instances automatically

✅ EC2 instances scale dynamically based on load

✅ Reduced manual intervention; automated monitoring & scaling
