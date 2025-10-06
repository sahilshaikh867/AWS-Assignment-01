# ☁️ AWS CloudWatch Agent Setup on EC2  

A step-by-step guide to install, configure, and monitor system-level metrics (CPU, memory, disk, and logs) on EC2 instances using **Amazon CloudWatch Agent**.

---

## 🎯 Objective  

- Install and configure the **CloudWatch Agent** on an EC2 instance  
- Collect **custom metrics** (like memory and disk usage) beyond default metrics  
- Send logs and metrics to **CloudWatch Dashboard**  
- Verify the data flow and performance  

---

## 🧰 Tools & Services Used  

| Service | Purpose |
|----------|----------|
| 💻 **Amazon EC2** | Host instance for agent installation |
| ☁️ **CloudWatch** | Collects and visualizes metrics |
| 🔐 **IAM Role** | Grants permissions to publish metrics |
| 📊 **CloudWatch Agent** | Collects OS-level metrics |
| 🪣 **S3 / CloudWatch Logs** | Optional: store logs centrally |

---

## 🪜 Step-by-Step Implementation  

### 1️⃣ Create IAM Role for EC2  

1. Go to **IAM → Roles → Create Role**  
2. Select **AWS Service** → choose **EC2**  
3. Attach the following policies:  
   - `CloudWatchAgentServerPolicy`  
   - `AmazonSSMManagedInstanceCore`  
4. Name the role: `EC2CloudWatchAgentRole`  
5. Click **Create Role**

📸 *Screenshot:* `screenshots/iam-role.png`

---

### 2️⃣ Attach Role to EC2 Instance  

1. Navigate to **EC2 → Instances**  
2. Select your instance → **Actions → Security → Modify IAM Role**  
3. Choose `EC2CloudWatchAgentRole` → **Apply**

📸 *Screenshot:* `screenshots/attach-role.png`

---

### 3️⃣ Connect to EC2 Instance  

Use **EC2 Instance Connect** or **SSH** from your terminal:  

```bash
ssh -i "keypair.pem" ec2-user@<Public-IP>
````

---

### 4️⃣ Install CloudWatch Agent

Run the following commands on your EC2 instance:

```bash
sudo yum update -y
sudo yum install amazon-cloudwatch-agent -y
```

📸 *Screenshot:* `screenshots/install-agent.png`

---

### 5️⃣ Create Configuration File

You can auto-generate one using the interactive wizard:

```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
```

🧩 During setup, choose:

* Metrics to collect → CPU, memory, disk, etc.
* Destination → CloudWatch
* Interval → 60 seconds
* Logs → Optional

When done, it saves a JSON config file at:
`/opt/aws/amazon-cloudwatch-agent/bin/config.json`

📸 *Screenshot:* `screenshots/config-wizard.png`

---

### 6️⃣ Start the CloudWatch Agent

Once configured, start the service:

```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
-a fetch-config \
-m ec2 \
-c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json \
-s
```

📸 *Screenshot:* `screenshots/start-agent.png`

To verify it’s running:

```bash
sudo systemctl status amazon-cloudwatch-agent
```

📸 *Screenshot:* `screenshots/agent-status.png`

---

### 7️⃣ Verify Metrics in CloudWatch

1. Go to **AWS Console → CloudWatch → Metrics → All metrics**
2. Under “Custom Namespaces”, find your instance metrics
3. You’ll see:

   * `mem_used_percent`
   * `disk_used_percent`
   * `cpu_usage_idle`
   * `swap_used_percent`
   * etc.

📸 *Screenshot:* `screenshots/metrics-dashboard.png`

---

### 8️⃣ (Optional) Send Logs to CloudWatch Logs

Edit the agent config file to include log file paths:

```json
{
  "logs": {
    "logs_collected": {
      "files": {
        "collect_list": [
          {
            "file_path": "/var/log/messages",
            "log_group_name": "EC2-SystemLogs",
            "log_stream_name": "{instance_id}"
          }
        ]
      }
    }
  }
}
```

Restart the agent to apply changes:

```bash
sudo systemctl restart amazon-cloudwatch-agent
```

📸 *Screenshot:* `screenshots/logs-upload.png`

---

### 9️⃣ Create CloudWatch Dashboard

1. Navigate to **CloudWatch → Dashboards → Create Dashboard**
2. Add widgets for metrics like CPU, Memory, Disk, etc.
3. Set refresh interval to **1 minute**

📸 *Screenshot:* `screenshots/dashboard.png`

---

### 🔟 (Optional) Stress Test CPU to Verify

Install `stress` tool to simulate high CPU load:

```bash
sudo amazon-linux-extras install epel -y
sudo yum install stress -y
stress --cpu 4 --timeout 120
```

📸 *Screenshot:* `screenshots/cpu-test.png`

Now go back to **CloudWatch → Metrics**, and you’ll see CPU usage spike 🚀

---

## 📊 Expected Output

| Metric              | Description                 | Result |
| ------------------- | --------------------------- | ------ |
| `CPUUtilization`    | Monitors processor usage    | ✅      |
| `mem_used_percent`  | Monitors memory utilization | ✅      |
| `disk_used_percent` | Tracks disk space           | ✅      |
| `log upload`        | Sends logs to CloudWatch    | ✅      |
| `dashboard`         | Real-time monitoring panel  | ✅      |

📸 *Screenshot:* `screenshots/final-dashboard.png`

---

## 🧠 Key Takeaways

| Concept                    | Description                             |
| -------------------------- | --------------------------------------- |
| **Custom Metrics**         | Add visibility beyond default EC2 stats |
| **Agent-Based Monitoring** | Real-time system-level data             |
| **IAM Role Permissions**   | Secure CloudWatch access                |
| **Dashboards & Alerts**    | Visualize and automate monitoring       |

---

## 🏁 Conclusion

✅ Installed and configured CloudWatch Agent successfully
✅ Collected custom metrics and logs
✅ Verified real-time updates on the CloudWatch dashboard
✅ Set foundation for advanced monitoring and automation

> 💡 *Next Step:* Integrate this with **Auto Scaling Group + Alarm** for fully automated scaling and alerts.

---

## 📂 Project Structure

```bash
📦 aws-cloudwatch-agent/
├── screenshots/
│   ├── iam-role.png
│   ├── attach-role.png
│   ├── install-agent.png
│   ├── config-wizard.png
│   ├── start-agent.png
│   ├── agent-status.png
│   ├── metrics-dashboard.png
│   ├── logs-upload.png
│   ├── cpu-test.png
│   └── final-dashboard.png
└── README.md
```
