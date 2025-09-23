# AWS Assignment 01

## Overview
This repository contains practical exercises and documentation for AWS services.  
The tasks cover: IAM, MFA, S3, EC2, VPC, Lambda, CloudWatch, Load Balancer, and EBS.  
Screenshots are included wherever applicable.

---

# **Task 1: IAM**

## Overview
IAM (Identity and Access Management) allows you to control **who can access your AWS account** and **what actions they can perform**.  

### Steps:
1. Search for IAM service in AWS console  
2. View IAM dashboard  
3. List and manage existing users  
4. Create new user with required permissions  
5. Enable console access (if needed)  
6. Enable MFA for extra security  

**Screenshots (placeholders)**:  
`iam-screenshots/first.png`, `ss1.png`, `user.png`, `ss3.png`, etc.

---

# **Task 2: MFA**

## Overview
Enable MFA (Multi-Factor Authentication) for IAM users to add an extra layer of security.

### Steps:
1. Sign in as IAM user  
2. Go to Security credentials → Manage MFA  
3. Configure MFA using mobile app (QR code or manual key)  
4. Enter two consecutive codes to register  
5. Test MFA login  

**Screenshots (placeholders)**:  
`screenshots/mfa-step1.png`, `mfa-step2.png`, `mfa-step3.png`, etc.

---

# **Task 3: S3**

## Overview
Amazon S3 is a storage service. This task covers:  
- Creating buckets  
- Uploading objects  
- Setting permissions and policies  
- Versioning and lifecycle rules  

**Screenshots (placeholders)**:  
`s3-screenshots/bucket-create.png`, `s3-upload.png`, etc.

---

# **Task 4: EC2 & EBS**

## Overview
EC2 is AWS compute service and EBS provides persistent block storage. Tasks cover:  
- Launching EC2 instances  
- Configuring key pairs and security groups  
- Attaching EBS volumes  
- Taking snapshots  

**Screenshots (placeholders)**:  
`ec2-screenshots/launch-instance.png`, `ebs-attach.png`, etc.

---

# **Task 5: VPC & Networking**

## Overview
VPC allows network segmentation and control. Tasks cover:  
- Creating VPC, subnets, IGW, route tables  
- Setting up NAT, Security groups, NACLs  
- Peering connections  

**Screenshots (placeholders)**:  
`vpc-screenshots/vpc-setup.png`, `subnet.png`, etc.

---

# **Task 6: Lambda**

## Overview
AWS Lambda allows serverless execution. Tasks cover:  
- Creating functions  
- Assigning roles and permissions  
- Testing execution  

**Screenshots (placeholders)**:  
`lambda-screenshots/lambda-create.png`, `lambda-test.png`, etc.

---

# **Task 7: CloudWatch**

## Overview
CloudWatch is used for monitoring and logging. Tasks cover:  
- Creating alarms  
- Viewing metrics  
- Logs and dashboards  

**Screenshots (placeholders)**:  
`cloudwatch-screenshots/alarm.png`, `metrics.png`, etc.

---

# **Task 8: Load Balancer**

## Overview
Load Balancer distributes traffic across multiple instances. Tasks cover:  
- Creating ELB  
- Configuring listeners and target groups  
- Health checks  

**Screenshots (placeholders)**:  
`loadbalancer-screenshots/create-lb.png`, `healthcheck.png`, etc.

---

## Notes / Best Practices
- Always follow **least privilege principle**  
- Keep credentials secure  
- Enable **MFA** for all IAM users  
- Take regular backups (EBS snapshots, S3 versioning)  
- Monitor resources using CloudWatch  

