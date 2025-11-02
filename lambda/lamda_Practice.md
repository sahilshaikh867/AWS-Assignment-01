## ⚡ **Part 2: AWS Lambda — Serverless Computing**

### 💡 What Lambda Actually Is

AWS Lambda lets you **run code without managing servers**.
No EC2 setup, no patching, no scaling headaches. You just:

1. Write your function (Python, Node.js, etc.)
2. Upload it or write it in the AWS Console
3. Set a **trigger** (like S3 file upload, API call, or CloudWatch event)
4. AWS runs it **only when needed**

You’re billed only for the **execution time**, not idle time.
So yeah — pure efficiency 👇

> **Code runs → job done → AWS auto-shuts it down.**

---

### 🧠 Key Concepts

| Concept            | Meaning                                                                                           |
| ------------------ | ------------------------------------------------------------------------------------------------- |
| **Function**       | The code you want to run (like a Python script).                                                  |
| **Event**          | The trigger — something that causes your function to execute (S3 upload, API Gateway call, etc.). |
| **Handler**        | The function entry point (e.g., `lambda_handler(event, context)`).                                |
| **Runtime**        | The language environment (Python, Node.js, Go, etc.).                                             |
| **Execution Role** | An IAM role that defines what your Lambda can access (like S3 buckets).                           |
| **Concurrency**    | How many functions can run simultaneously.                                                        |

---

### ⚙️ Step-by-Step Hands-On (Console)

#### 1️⃣ Go to Lambda Console

👉 [AWS Lambda Console](https://console.aws.amazon.com/lambda/home)

#### 2️⃣ Create a New Function

* Click **“Create function”**
* Choose **Author from scratch**
* Function name: `s3-lambda-demo`
* Runtime: **Python 3.x**
* Permissions:
  → Choose **Create a new role with basic Lambda permissions**

Click **Create function**

---

#### 3️⃣ Add Some Code

In the inline editor, replace everything with this simple example 👇

```python
import json

def lambda_handler(event, context):
    print("Event received from S3:")
    print(json.dumps(event, indent=2))
    return {
        'statusCode': 200,
        'body': json.dumps('Lambda is connected to S3 successfully!')
    }
```

Click **Deploy**

---

#### 4️⃣ Add an S3 Trigger

* Scroll down → **Add trigger**
* Choose **S3**
* Select your S3 bucket (e.g., `sahil-learning-bucket`)
* Event type: **All object create events**
* Save

Now, every time you upload a new file to that bucket, Lambda will automatically trigger and log the event.

---

#### 5️⃣ Test the Setup

* Go back to S3 → upload a new file (like `trigger-test.txt`)
* Go to Lambda → **Monitor → View logs in CloudWatch**
* You’ll see a log entry with the event details!

---

### ✅ You Just Built:

A fully **event-driven serverless setup**:

> S3 (data input) → triggers → Lambda (code execution)

This combo is used everywhere — from **image processing pipelines** to **data ETL**, **notifications**, and even **AI workflows**.

---

### 🧩 Bonus Ideas

* Add another Lambda to **resize images** when uploaded.
* Send an email via **Amazon SNS** when a new file arrives.
* Store file metadata in **DynamoDB**.

---

  
