# 🚀 AWS Assignment  

This repository contains AWS practical tasks performed as part of the assignment.  
Each section has short information about completed tasks.  

---

## 🧑‍💻 IAM  
1. **Enable MFA for IAM User** → Enabled MFA using AWS Console.  
2. **Create IAM User with CLI Access** → Created programmatic user with AWS CLI access.  

---

## 🖥️ EC2 & EBS  
1. **Install AWS CLI on Ubuntu** → Installed and verified AWS CLI.  
2. **Create AMI & Launch Instance** → Created AMI and launched new EC2.  
3. **Custom Security Group (only my IP)** → Configured inbound rules for single IP access.  
4. **Create & Mount Volume** → Attached EBS and mounted it on EC2 instance.  
5. **Recover EC2 Access** → Recovered access after key pair was lost.  
6. **Take EBS Snapshot & Restore** → Created snapshot and restored volume.  

---

## ☁️ S3  
1. **Host Static Website** → Hosted sample HTML on S3 bucket.  
2. **Enable Versioning & Restore** → Enabled versioning and restored deleted objects.  
3. **Upload Multiple Versions** → Uploaded file with multiple versions.  
4. **Pre-signed URL** → Generated temporary URL for file sharing.  
5. **Server Access Logging** → Enabled server access logging on bucket.  
6. **Trigger Lambda on Upload** → Configured Lambda to send email via SNS on upload.  
7. **Cross-region Access** → Set up S3 cross-region replication.  

---

## 📊 CloudWatch & Auto Scaling  
1. **CloudWatch Alarm (CPU ≥ 50%)** → Configured alarm for EC2 CPU usage.  
2. **Auto Scaling with CloudWatch** → Configured ASG linked with CloudWatch alarm.  

---

## 🌐 VPC & Networking  
1. **VPC Peering** → Setup peering in same region and cross region.  
2. **3-Tier Architecture** → Designed VPC with public, private, and DB subnets.  
3. **VPC Endpoint for S3** → Configured endpoint for private S3 access.  
4. **Subnetting** → Divided CIDR 172.21.0.0/16 into /17 to /23 ranges.  

---

## ⚖️ Load Balancing  
1. **Host Template on Nginx & HTTPD** → Deployed same site on both servers.  
2. **Application Load Balancer** → Configured ALB for traffic distribution.  

---

## 🪄 Lambda  
1. **Trigger on S3 Upload (via SNS Email)** → Automated email notifications using Lambda + SNS.  
2. **Scheduled EC2 Start/Stop** → Configured Lambda to start/stop EC2 on schedule.  

---

## 📂 Folder Structure  

📦 aws-assignment  
 ┣ 📂 iam  
 ┃ ┗ 📜 README.md       # IAM tasks summary  
 ┣ 📂 ec2-ebs  
 ┃ ┗ 📜 README.md       # EC2 & EBS tasks summary  
 ┣ 📂 s3  
 ┃ ┗ 📜 README.md       # S3 tasks summary  
 ┣ 📂 cloudwatch  
 ┃ ┗ 📜 README.md       # CloudWatch & Auto Scaling tasks summary  
 ┣ 📂 vpc  
 ┃ ┗ 📜 README.md       # VPC & Networking tasks summary  
 ┣ 📂 loadbalancer  
 ┃ ┗ 📜 README.md       # Load Balancing tasks summary  
 ┣ 📂 lambda  
 ┃ ┗ 📜 README.md       # Lambda tasks summary  
 ┗ 📜 README.md         # Main assignment file (all tasks short info)  
