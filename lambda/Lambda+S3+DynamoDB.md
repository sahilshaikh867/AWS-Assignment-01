# ⚡ AWS Lambda + S3 + DynamoDB Combined Workflow  

A complete **serverless project** that integrates **AWS Lambda**, **S3**, and **DynamoDB** to build an event-driven data pipeline.  

Whenever a file is uploaded to an S3 bucket:
- Lambda is automatically triggered 🧠  
- File metadata is extracted 📄  
- Metadata is stored in DynamoDB 🔥  

---

## 🎯 Objective  

- Build an **automated metadata tracker** for S3 uploads  
- Use **Lambda triggers** to automate DynamoDB entries  
- Gain hands-on with **event-driven architectures** on AWS  

---

## 🧰 Tools & Services Used  

| Service | Purpose |
|----------|----------|
| 🪣 **Amazon S3** | Stores uploaded files |
| 🧠 **AWS Lambda** | Executes logic automatically on S3 upload |
| 🗃️ **DynamoDB** | Stores file metadata (name, size, timestamp) |
| 📊 **CloudWatch** | Logs and monitoring |
| 🐍 **Python 3.9** | Lambda runtime |

---

## 🪜 Step-by-Step Implementation  

### 1️⃣ Create an S3 Bucket  

1. Go to **AWS Console → S3 → Create Bucket**  
2. Bucket name: `lambda-s3-dynamo-demo`  
3. Region: `ap-south-1`  
4. Leave permissions as private  
5. Click **Create bucket**

📸 *Screenshot:* `screenshots/s3-create.png`

---

### 2️⃣ Create a DynamoDB Table  

1. Navigate to **AWS Console → DynamoDB → Create Table**  
2. Table name → `FileMetadata`  
3. Primary key → `file_name` (String)  
4. Leave default settings and **Create Table**  

📸 *Screenshot:* `screenshots/dynamodb-create.png`

---

### 3️⃣ Create a Lambda Function  

1. Go to **AWS Lambda → Create Function**  
2. Choose **Author from Scratch**  
3. Function name → `S3ToDynamoLambda`  
4. Runtime → `Python 3.9`  
5. Execution Role → Create new role with:
   - `AmazonS3FullAccess`
   - `AmazonDynamoDBFullAccess`
   - `CloudWatchLogsFullAccess`  

📸 *Screenshot:* `screenshots/lambda-create.png`

---

### 4️⃣ Add Code to Lambda  

```python
import json
import boto3
from datetime import datetime

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('FileMetadata')

def lambda_handler(event, context):
    try:
        # Extract S3 event details
        for record in event['Records']:
            bucket_name = record['s3']['bucket']['name']
            file_name = record['s3']['object']['key']
            file_size = record['s3']['object'].get('size', 0)

            # Store metadata in DynamoDB
            table.put_item(
                Item={
                    'file_name': file_name,
                    'bucket': bucket_name,
                    'size': file_size,
                    'uploaded_at': datetime.utcnow().isoformat()
                }
            )

        return {
            'statusCode': 200,
            'body': json.dumps('Metadata stored successfully!')
        }

    except Exception as e:
        print("Error:", e)
        return {
            'statusCode': 500,
            'body': json.dumps('Error processing file metadata')
        }
````

📸 *Screenshot:* `screenshots/lambda-code.png`

---

### 5️⃣ Add S3 Trigger to Lambda

1. In your Lambda Function → Click **Add Trigger**
2. Choose **S3**
3. Select your bucket → `lambda-s3-dynamo-demo`
4. Event type → `PUT` (Object Created)
5. Click **Add**

📸 *Screenshot:* `screenshots/lambda-trigger.png`

💡 Now every time a file is uploaded, the Lambda function will automatically trigger!

---

### 6️⃣ Test the Flow

1. Go to **S3 → Your Bucket → Upload File**
2. Upload a file (e.g., `demo.txt`)
3. Go to **DynamoDB → FileMetadata → Explore Table Items**
4. Verify that metadata (file name, size, timestamp) was stored successfully

📸 *Screenshot:* `screenshots/dynamodb-verify.png`

---

### 7️⃣ Verify Logs

* Navigate to **CloudWatch → Logs → /aws/lambda/S3ToDynamoLambda**
* Check for successful trigger logs

📸 *Screenshot:* `screenshots/cw-logs.png`

---

## 📂 Repository Structure

```bash
📦 aws-lambda-s3-dynamo/
├── lambda_function.py
├── screenshots/
│   ├── s3-create.png
│   ├── dynamodb-create.png
│   ├── lambda-create.png
│   ├── lambda-code.png
│   ├── lambda-trigger.png
│   ├── dynamodb-verify.png
│   └── cw-logs.png
└── README.md
```

---

## 🧠 How It Works

1. User uploads file to S3
2. S3 event triggers Lambda
3. Lambda extracts file details
4. Lambda stores file metadata in DynamoDB
5. CloudWatch logs confirm event flow

📊 **Architecture Flow:**

```
[ User Upload ] → [ S3 Bucket ] → [ Lambda Trigger ] → [ DynamoDB Entry ] → [ CloudWatch Logs ]
```

---

## 🧩 Key Concepts

| Concept                 | Description                              |
| ----------------------- | ---------------------------------------- |
| **Event-driven design** | Lambda reacts automatically to S3 events |
| **Serverless pipeline** | Fully managed, no servers involved       |
| **Data persistence**    | File metadata stored in DynamoDB         |
| **Scalability**         | Automatically scales with upload volume  |

---

## 🌟 Expected Output

| Step           | Description               | Status |
| -------------- | ------------------------- | ------ |
| S3 Bucket      | Created and file uploaded | ✅      |
| Lambda Trigger | Auto executed             | ✅      |
| DynamoDB       | File metadata stored      | ✅      |
| CloudWatch     | Logs captured             | ✅      |

📸 *Screenshot:* `screenshots/final-output.png`

---

## 🧠 Future Enhancements

* Add **SNS Notification** for each new upload 📩
* Store file type and checksum for validation
* Add **API Gateway endpoint** for metadata retrieval
* Build **Athena Query Dashboard** for insights

---

## 🌐 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge\&logo=linkedin\&logoColor=white)](https://www.linkedin.com/in/sahilshaikh867/)
[![Portfolio](https://img.shields.io/badge/Portfolio-grey?style=for-the-badge\&logo=vercel\&logoColor=white)](https://sahilshaikh867.vercel.app/)

---

## 🏁 Final Outcome

✅ Serverless pipeline built successfully
✅ File upload triggers automatic metadata storage
✅ Zero infrastructure management required
✅ Fully event-driven, scalable workflow

> 💬 *This is how modern data pipelines work — automated, reliable, and 100% cloud-native.*
