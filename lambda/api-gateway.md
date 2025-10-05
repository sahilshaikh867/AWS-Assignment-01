# 🌐 AWS Lambda + API Gateway Integration Project  

Welcome to my **Serverless API Project** built using **AWS Lambda** and **Amazon API Gateway** ⚡  
This project demonstrates how to deploy a fully functional REST API without managing servers — using AWS’s serverless ecosystem.  

---

## 📌 Objective  

- Create an **AWS Lambda function** to process requests  
- Use **Amazon API Gateway** as the front door for the function  
- Test the API via **browser / Postman / CLI**  
- Analyze results and logs via **CloudWatch**

---

## 🛠️ Tools & Technologies  

| Tool | Purpose |
|------|----------|
| 🧠 **AWS Lambda** | Backend logic execution |
| 🌐 **API Gateway** | REST API endpoint management |
| 🧾 **CloudWatch** | Log monitoring |
| 🐍 **Python 3.9** | Function runtime |
| 💻 **AWS Console / CLI** | Setup & deployment |

---

## 🪜 Step-by-Step Implementation  

### 1️⃣ Create a Lambda Function  

1. Go to **AWS Console → Lambda → Create Function**  
2. Choose **Author from scratch**  
3. Function name → `serverlessApiLambda`  
4. Runtime → `Python 3.9`  
5. Role → Create new with basic Lambda permissions (`AWSLambdaBasicExecutionRole`)  
6. Click **Create Function**  

📸 *Screenshot:* `lambda-api-create.png`

---

### 2️⃣ Add Lambda Code  

In the **Code Source** editor, paste this code 👇  

```python
import json

def lambda_handler(event, context):
    name = event.get('queryStringParameters', {}).get('name', 'Stranger')
    message = f"Hello, {name}! Welcome to your Serverless API 🎉"
    
    return {
        'statusCode': 200,
        'headers': {'Content-Type': 'application/json'},
        'body': json.dumps({'message': message})
    }
````

📸 *Screenshot:* `lambda-api-code.png`

💡 **Tip:**
You can modify this logic — e.g., read from S3, DynamoDB, or return custom data structures.

---

### 3️⃣ Deploy an API Gateway

1. Navigate to **API Gateway → Create API**
2. Choose **REST API → Build**
3. Click **Create Resource** → name it `/greet`
4. Click **Create Method → GET**
5. Select **Integration type:** *Lambda Function*
6. Choose your Lambda → `serverlessApiLambda`
7. Click **Save** → confirm permissions prompt

📸 *Screenshot:* `api-gateway-setup.png`

---

### 4️⃣ Deploy the API

1. In API Gateway sidebar → **Actions → Deploy API**
2. Create a **new stage**, e.g. `dev`
3. Copy the **Invoke URL**, something like:

   ```
   https://xyz123.execute-api.ap-south-1.amazonaws.com/dev/greet
   ```

📸 *Screenshot:* `api-gateway-deploy.png`

---

### 5️⃣ Test the API Endpoint

#### ✅ Using Browser:

Visit the URL:

```
https://xyz123.execute-api.ap-south-1.amazonaws.com/dev/greet?name=Sahil
```

Output:

```json
{
  "message": "Hello, Sahil! Welcome to your Serverless API 🎉"
}
```

#### ✅ Using Postman / curl:

```bash
curl "https://xyz123.execute-api.ap-south-1.amazonaws.com/dev/greet?name=Sahil"
```

📸 *Screenshot:* `api-test.png`

---

### 6️⃣ Check Logs in CloudWatch

* Navigate to **CloudWatch → Logs → Log groups → /aws/lambda/serverlessApiLambda**
* View latest log stream for execution details

📸 *Screenshot:* `api-logs.png`

---

## ⚡ Bonus: Add a POST Method

You can also accept JSON body data!

```python
def lambda_handler(event, context):
    body = json.loads(event.get('body', '{}'))
    user = body.get('user', 'Anonymous')
    
    return {
        'statusCode': 200,
        'body': json.dumps({'message': f"Hello {user}, this is a POST response!"})
    }
```

📸 *Screenshot:* `api-post.png`

---

## 📊 Outputs Summary

| Step                 | Description          | Status |
| -------------------- | -------------------- | ------ |
| Lambda Function      | Created successfully | ✅      |
| API Gateway Resource | Connected to Lambda  | ✅      |
| API Deployed         | Endpoint active      | ✅      |
| CloudWatch Logs      | Verified execution   | ✅      |

---

## 📂 Suggested Repository Structure

```bash
📦 aws-lambda-api-project/
├── lambda_function.py
├── screenshots/
│   ├── lambda-api-create.png
│   ├── lambda-api-code.png
│   ├── api-gateway-setup.png
│   ├── api-gateway-deploy.png
│   ├── api-test.png
│   ├── api-logs.png
│   └── api-post.png
└── README.md  👈 (This file)
```

---

## 🧠 Key Takeaways

* 🔥 **AWS Lambda + API Gateway** = Serverless REST API
* ⚙️ No infrastructure to manage — AWS handles scaling
* 🪶 Pay only for execution time
* 🧾 Logs auto-integrate with CloudWatch
* 💡 Perfect foundation for microservices or CI/CD triggers

---

## 🌐 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge\&logo=linkedin\&logoColor=white)](https://www.linkedin.com/in/sahilshaikh867/)
[![Portfolio](https://img.shields.io/badge/Portfolio-grey?style=for-the-badge\&logo=vercel\&logoColor=white)](https://sahilshaikh867.vercel.app/)

---

## 🎯 Goal

By the end of this project, I successfully:

* Created a Lambda-based backend
* Integrated it with API Gateway for HTTP access
* Tested API responses and logs
* Built a production-style **serverless microservice** 💥

Next up → **Lambda + DynamoDB Integration Project 🔜**
