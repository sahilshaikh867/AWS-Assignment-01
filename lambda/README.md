# ⚡ AWS Lambda Function Practice

Welcome to my **AWS Lambda Practice Lab** 💻  
In this hands-on session, I created, tested, and deployed a **Lambda Function** using AWS Console and CLI — covering all the key configurations step-by-step.

---

## 📌 Overview

AWS **Lambda** is a **serverless compute service** that runs your code in response to events — without provisioning or managing servers.  
You just upload the code, set a trigger, and AWS takes care of the rest. 🪄  

---

## 🪜 Step-by-Step Implementation

### 1️⃣ Create a Lambda Function

1. Go to **AWS Management Console → Lambda**
2. Click **Create function**
3. Choose **Author from scratch**
4. Enter function name: `helloLambda`
5. Choose runtime: `Python 3.9` (you can also select Node.js or Java)
6. Select or create an **execution role** with permissions:
   - `AWSLambdaBasicExecutionRole`
7. Click **Create function**

📸 *Screenshot Suggestion:* `lambda-create.png`

---

### 2️⃣ Write Your Code

In the Lambda code editor, replace the default code with:

```python
def lambda_handler(event, context):
    message = "Hello from AWS Lambda!"
    print(message)
    return {
        'statusCode': 200,
        'body': message
    }
````

📸 *Screenshot Suggestion:* `lambda-code.png`

💡 **Tip:** You can test it directly in the console using the “Test” button.

---

### 3️⃣ Create a Test Event

1. Click **Test** → “Configure test event”
2. Choose “Create new test event”
3. Name it `testEvent`
4. Use the following sample event JSON:

   ```json
   {
     "key1": "value1",
     "key2": "value2"
   }
   ```
5. Click **Save and Test**

📸 *Screenshot Suggestion:* `lambda-test.png`

---

### 4️⃣ Verify Execution

* You’ll see the **Execution result: succeeded ✅**
* Check the **Log output** to confirm the message:
  `"Hello from AWS Lambda!"`
* Check the **CloudWatch Logs** to view the log stream.

📸 *Screenshot Suggestion:* `lambda-success.png`

---

### 5️⃣ Add a Trigger (Optional)

Let’s connect your Lambda function with a trigger, like **S3 or API Gateway**.

#### 🧩 Example 1: S3 Trigger

* Go to your **S3 bucket**
* Click **Properties → Event Notifications**
* Add a new event to trigger Lambda on file upload

#### 🌐 Example 2: API Gateway Trigger

* Go to **API Gateway → Create API → REST API**
* Integrate your Lambda function
* Deploy and test your API endpoint

📸 *Screenshot Suggestion:* `lambda-trigger.png`

---

### 6️⃣ Update Lambda Function via AWS CLI (Optional)

You can update your Lambda function directly from CLI.

```bash
aws lambda update-function-code \
    --function-name helloLambda \
    --zip-file fileb://function.zip
```

📸 *Screenshot Suggestion:* `lambda-cli.png`

---

## 📊 Outputs

| Step              | Description                 | Status |
| ----------------- | --------------------------- | ------ |
| Function Creation | Lambda created successfully | ✅      |
| Test Execution    | Output returned properly    | ✅      |
| Logs Generated    | CloudWatch logs verified    | ✅      |
| Trigger Added     | (If configured) Works fine  | ✅      |

---

## 🧠 Key Takeaways

* Lambda is **event-driven** — triggers can be from S3, SNS, CloudWatch, etc.
* You **don’t need servers** — AWS handles scaling & infra.
* Logs are auto-sent to **CloudWatch**.
* Billing is based on **execution time**, not instance uptime.

---

## 📂 Suggested Repository Structure

```bash
📦 aws-lambda/
├── lambda-function.py
├── screenshots/
│   ├── lambda-create.png
│   ├── lambda-code.png
│   ├── lambda-test.png
│   ├── lambda-success.png
│   ├── lambda-trigger.png
│   └── lambda-cli.png
└── README.md  👈 (This file)
```

---

## 🌐 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge\&logo=linkedin\&logoColor=white)](https://www.linkedin.com/in/sahilshaikh867/)
[![Portfolio](https://img.shields.io/badge/Portfolio-grey?style=for-the-badge\&logo=vercel\&logoColor=white)](https://sahilshaikh867.vercel.app/)

---

## 🎯 Goal

By the end of this practice, I successfully:

* Created & executed my first Lambda Function 🧠
* Tested it via Console & CloudWatch Logs
* Understood integration with S3 & API Gateway
* Managed function updates using CLI

Next up → **Lambda + API Gateway Integration Project 🚀**

