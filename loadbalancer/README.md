# ⚖️ AWS Load Balancer Project  

A hands-on project to deploy a **Load Balancer** that distributes incoming traffic across multiple EC2 instances for high availability, fault tolerance, and scalability.

---

## 🎯 Objective  

- Deploy **2 EC2 instances** with a web server (Apache or Nginx)  
- Configure an **Application Load Balancer (ALB)**  
- Test how traffic is balanced between instances  
- Observe load balancing behavior when one instance stops  

---

## 🧰 Tools & Services Used  

| Service | Purpose |
|----------|----------|
| 💻 **Amazon EC2** | Backend web servers |
| ⚖️ **Elastic Load Balancer (ALB)** | Distributes incoming traffic |
| 🔒 **Security Groups** | Manage inbound/outbound rules |
| ☁️ **VPC & Subnets** | Networking environment |
| 📊 **CloudWatch** | Logs and performance metrics |

---

## 🪜 Step-by-Step Implementation  

### 1️⃣ Launch Two EC2 Instances  

1. Go to **EC2 Dashboard → Launch Instance**
2. Name: `web-server-1` and `web-server-2`
3. AMI: Amazon Linux 2 (Free Tier)
4. Instance type: `t2.micro`
5. Create or select a **Key Pair**
6. Add user data to install a web server automatically:

```bash
#!/bin/bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
echo "<h1>This is Web Server 1 - $(hostname)</h1>" > /var/www/html/index.html
````

📸 *Screenshot:* `screenshots/ec2-setup1.png`

👉 Repeat for **Web Server 2**, but change text to:

```bash
echo "<h1>This is Web Server 2 - $(hostname)</h1>" > /var/www/html/index.html
```

📸 *Screenshot:* `screenshots/ec2-setup2.png`

---

### 2️⃣ Configure Security Groups

* Create a new Security Group: `load-balancer-sg`
* Allow **HTTP (port 80)** and **SSH (port 22)** from your IP or Anywhere
* Attach this SG to both EC2 instances

📸 *Screenshot:* `screenshots/security-group.png`

---

### 3️⃣ Verify EC2 Instances

* Copy **Public IP** of each instance
* Open in browser:

  * `http://<PublicIP-of-WebServer1>`
  * `http://<PublicIP-of-WebServer2>`
* You should see each page with its respective message ✅

📸 *Screenshot:* `screenshots/ec2-test.png`

---

### 4️⃣ Create a Load Balancer

1. Go to **EC2 → Load Balancers → Create Load Balancer**
2. Choose **Application Load Balancer (ALB)**
3. Name: `my-app-load-balancer`
4. Scheme: **Internet-facing**
5. Listener: **HTTP (Port 80)**
6. Choose at least **2 Availability Zones**
7. Create a **Target Group** → Type: **Instances**

📸 *Screenshot:* `screenshots/alb-create.png`

---

### 5️⃣ Register Targets

1. Select your Target Group
2. Click **Register Targets**
3. Choose both EC2 instances (web-server-1, web-server-2)
4. Click **Include as pending below → Register targets**

📸 *Screenshot:* `screenshots/register-targets.png`

---

### 6️⃣ Test Load Balancer

1. Copy the **DNS Name** of your Load Balancer (e.g. `my-app-load-balancer-123456.ap-south-1.elb.amazonaws.com`)
2. Paste in browser multiple times (or use incognito tabs)
3. You’ll see responses alternating between:

   * `This is Web Server 1`
   * `This is Web Server 2`

📸 *Screenshot:* `screenshots/lb-test.png`

---

### 7️⃣ Stop One Instance (Failover Test)

* Stop **Web Server 1** from EC2 console
* Refresh the Load Balancer DNS URL again
* Traffic should automatically route to **Web Server 2**

📸 *Screenshot:* `screenshots/failover-test.png`

---

## 🧠 How It Works

```
         ┌────────────────────────────┐
         │        Internet User       │
         └────────────┬───────────────┘
                      │
             ┌────────▼────────┐
             │ Application LB  │
             └──────┬──────────┘
          ┌─────────┴────────────┐
          │                      │
┌─────────▼─────────┐   ┌────────▼─────────┐
│  Web Server 1     │   │  Web Server 2     │
│  EC2 Instance     │   │  EC2 Instance     │
└───────────────────┘   └───────────────────┘
```

---

## 📂 Project Structure

```bash
📦 aws-load-balancer/
├── scripts/
│   ├── web-server-1.sh
│   └── web-server-2.sh
├── screenshots/
│   ├── ec2-setup1.png
│   ├── ec2-setup2.png
│   ├── security-group.png
│   ├── alb-create.png
│   ├── register-targets.png
│   ├── lb-test.png
│   ├── failover-test.png
│   └── final-output.png
└── README.md
```

---

## 📊 Expected Output

| Step                 | Description           | Status |
| -------------------- | --------------------- | ------ |
| EC2 Setup            | 2 Web servers running | ✅      |
| Load Balancer        | Created & functional  | ✅      |
| Traffic Distribution | Working fine          | ✅      |
| Failover Test        | Successful            | ✅      |

📸 *Screenshot:* `screenshots/final-output.png`

---

## 🧠 Key Concepts

| Concept               | Description                            |
| --------------------- | -------------------------------------- |
| **High Availability** | Requests distributed across servers    |
| **Scalability**       | Add/remove instances dynamically       |
| **Fault Tolerance**   | Automatically reroutes on failure      |
| **Health Checks**     | Load balancer monitors instance health |

---

## 💡 Optional Add-ons

* Enable **HTTPS (SSL)** using ACM certificate
* Configure **Auto Scaling Group (ASG)** with the Load Balancer
* Monitor load using **CloudWatch metrics**
* Add custom domain using **Route 53**

---

## 🏁 Conclusion

✅ Successfully deployed a Load Balancer distributing traffic between multiple EC2 instances.
✅ Verified automatic traffic redirection when one instance goes down.
✅ Demonstrated real-world load balancing and fault tolerance in AWS.

> ⚙️ This setup is the backbone of modern scalable web apps — pure AWS power, no manual load management needed!
