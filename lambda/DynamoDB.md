# ⚡ AWS Lambda + DynamoDB Integration Project  

This project demonstrates how to build a **serverless backend** using **AWS Lambda** as compute and **Amazon DynamoDB** as the database — all without managing any servers or infrastructure! 🌩️  

---

## 📌 Objective  

- Create a **DynamoDB table** to store user data  
- Build a **Lambda function** to perform CRUD operations  
- Integrate the function with **API Gateway**  
- Test the REST API using **Postman / curl**  
- Verify logs using **CloudWatch**

---

## 🧰 Tools & Services  

| Tool | Purpose |
|------|----------|
| 🧠 **AWS Lambda** | Backend compute (serverless logic) |
| 🪣 **DynamoDB** | NoSQL database for data storage |
| 🌐 **API Gateway** | Exposes Lambda as REST API |
| 🔎 **CloudWatch** | Monitoring & logs |
| 🐍 **Python 3.9** | Lambda runtime |

---

## 🪜 Step-by-Step Implementation  

### 1️⃣ Create DynamoDB Table  

1. Go to **AWS Console → DynamoDB → Create table**  
2. Table name → `UsersTable`  
3. Partition key → `userId` (String)  
4. Keep other options default  
5. Click **Create Table**

📸 *Screenshot:* `ddb-create.png`

💡 **Tip:** You can also enable TTL or add indexes later for queries.

---

### 2️⃣ Create a Lambda Function  

1. Go to **AWS Console → Lambda → Create Function**  
2. Choose **Author from scratch**  
3. Function name → `LambdaDDBHandler`  
4. Runtime → `Python 3.9`  
5. Role → Create new with **basic Lambda permissions + DynamoDB full access**  
6. Click **Create Function**

📸 *Screenshot:* `lambda-create.png`

---

### 3️⃣ Add Code in Lambda  

Paste this sample CRUD code 👇  

```python
import boto3
import json
import uuid

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('UsersTable')

def lambda_handler(event, context):
    method = event['httpMethod']
    
    if method == 'POST':
        data = json.loads(event['body'])
        user_id = str(uuid.uuid4())
        table.put_item(Item={'userId': user_id, 'name': data['name'], 'email': data['email']})
        return {'statusCode': 200, 'body': json.dumps({'message': 'User added!', 'userId': user_id})}
    
    elif method == 'GET':
        user_id = event['queryStringParameters']['userId']
        response = table.get_item(Key={'userId': user_id})
        return {'statusCode': 200, 'body': json.dumps(response.get('Item', {}))}
    
    elif method == 'DELETE':
        user_id = event['queryStringParameters']['userId']
        table.delete_item(Key={'userId': user_id})
        return {'statusCode': 200, 'body': json.dumps({'message': 'User deleted successfully'})}
    
    else:
        return {'statusCode': 400, 'body': json.dumps({'error': 'Unsupported method'})}
````

📸 *Screenshot:* `lambda-code.png`

💡 **Note:** Replace `'UsersTable'` with your actual DynamoDB table name if different.

---

### 4️⃣ Integrate with API Gateway

1. Go to **API Gateway → Create API → REST API**
2. Create resource → `/users`
3. Add methods:

   * `POST` → Lambda integration
   * `GET` → Lambda integration
   * `DELETE` → Lambda integration
4. Deploy API → Stage name: `prod`
5. Copy invoke URL — e.g.

   ```
   https://xyz123.execute-api.ap-south-1.amazonaws.com/prod/users
   ```

📸 *Screenshot:* `api-setup.png`

---

### 5️⃣ Test the API

#### ✅ **POST Request (Add User)**

```bash
curl -X POST https://xyz123.execute-api.ap-south-1.amazonaws.com/prod/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Sahil", "email": "sahil@example.com"}'
```

Response:

```json
{
  "message": "User added!",
  "userId": "a1b2c3d4"
}
```

📸 *Screenshot:* `api-post-test.png`

---

#### ✅ **GET Request (Fetch User)**

```bash
curl "https://xyz123.execute-api.ap-south-1.amazonaws.com/prod/users?userId=a1b2c3d4"
```

Response:

```json
{
  "userId": "a1b2c3d4",
  "name": "Sahil",
  "email": "sahil@example.com"
}
```

📸 *Screenshot:* `api-get-test.png`

---

#### ✅ **DELETE Request (Remove User)**

```bash
curl -X DELETE "https://xyz123.execute-api.ap-south-1.amazonaws.com/prod/users?userId=a1b2c3d4"
```

Response:

```json
{
  "message": "User deleted successfully"
}
```

📸 *Screenshot:* `api-delete-test.png`

---

### 6️⃣ Verify Data in DynamoDB

* Go to **AWS Console → DynamoDB → Tables → UsersTable → Explore Table Items**
* You should see your records appear and disappear as per requests

📸 *Screenshot:* `ddb-data.png`

---

### 7️⃣ Check CloudWatch Logs

* Navigate to **CloudWatch → Logs → Log groups → /aws/lambda/LambdaDDBHandler**
* Verify event logs for each API hit

📸 *Screenshot:* `logs.png`

---

## 📂 Repository Structure

```bash
📦 aws-lambda-dynamodb/
├── lambda_function.py
├── screenshots/
│   ├── ddb-create.png
│   ├── lambda-create.png
│   ├── lambda-code.png
│   ├── api-setup.png
│   ├── api-post-test.png
│   ├── api-get-test.png
│   ├── api-delete-test.png
│   ├── ddb-data.png
│   └── logs.png
└── README.md
```

---

## 🧠 Key Learnings

* 🔥 Combined **Lambda** compute power with **DynamoDB** persistence
* 🌐 Created a fully **serverless CRUD API**
* 🪶 No servers, no maintenance, automatic scaling
* 💸 Pay only for usage
* ⚙️ Perfect for microservices, IoT, or small backend apps

---

## 📊 Outputs Summary

| Step            | Description             | Status |
| --------------- | ----------------------- | ------ |
| DynamoDB Table  | Created                 | ✅      |
| Lambda Function | Connected to DynamoDB   | ✅      |
| API Gateway     | Integrated successfully | ✅      |
| CRUD Operations | Working and tested      | ✅      |
| CloudWatch Logs | Verified                | ✅      |

---

## 🌟 Future Enhancements

* Add **PUT** (update) method
* Add **error handling** and validation
* Integrate **IAM policy restriction**
* Trigger Lambda from **S3 / EventBridge**
* Add **frontend (React)** for UI testing

---

## 🌐 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge\&logo=linkedin\&logoColor=white)](https://www.linkedin.com/in/sahilshaikh867/)
[![Portfolio](https://img.shields.io/badge/Portfolio-grey?style=for-the-badge\&logo=vercel\&logoColor=white)](https://sahilshaikh867.vercel.app/)

---

## 🎯 Final Outcome

✅ **Lambda** runs code on demand
✅ **DynamoDB** stores data seamlessly
✅ **API Gateway** exposes endpoints
✅ **CloudWatch** monitors logs
✅ **Serverless architecture achieved** 🚀

> Next Up → AWS Lambda + S3 File Upload Project 📦✨
