# ☁️ AWS Lambda + S3 File Upload Project  

This project demonstrates how to upload files directly to **Amazon S3** using an **AWS Lambda function** triggered via **API Gateway**.  
Perfect for serverless apps that need lightweight file storage without EC2 or backend servers. 🚀  

---

## 📌 Objective  

- Create an **S3 bucket** for file storage  
- Create a **Lambda function** to handle file uploads  
- Integrate with **API Gateway** to expose an upload endpoint  
- Test uploads using **Postman / curl**  
- Verify results and logs via **CloudWatch**  

---

## 🧰 Tools & Services  

| Tool | Purpose |
|------|----------|
| 🧠 **AWS Lambda** | Backend compute for processing uploads |
| 🪣 **Amazon S3** | File storage |
| 🌐 **API Gateway** | Expose upload API |
| 🔎 **CloudWatch** | Monitor logs |
| 🐍 **Python 3.9** | Lambda runtime |

---

## 🪜 Step-by-Step Implementation  

### 1️⃣ Create an S3 Bucket  

1. Navigate to **AWS Console → S3 → Create Bucket**  
2. Bucket name: `lambda-upload-bucket-demo`  
3. Region: `ap-south-1`  
4. Uncheck “Block all public access” (only if needed for demo)  
5. Click **Create bucket**

📸 *Screenshot:* `s3-create.png`

💡 **Tip:** Keep the bucket private for security; use pre-signed URLs if sharing.

---

### 2️⃣ Create a Lambda Function  

1. Go to **AWS Lambda → Create Function**  
2. Choose **Author from scratch**  
3. Function name → `S3FileUploadLambda`  
4. Runtime → `Python 3.9`  
5. Role → Create new role with **S3 full access** and **CloudWatch logging**  
6. Click **Create Function**

📸 *Screenshot:* `lambda-create.png`

---

### 3️⃣ Add Code in Lambda  

Paste this Python code 👇  

```python
import json
import base64
import boto3
import uuid

s3 = boto3.client('s3')
BUCKET_NAME = 'lambda-upload-bucket-demo'

def lambda_handler(event, context):
    try:
        body = json.loads(event['body'])
        file_content = base64.b64decode(body['file'])
        file_name = f"{uuid.uuid4()}_{body['filename']}"

        s3.put_object(Bucket=BUCKET_NAME, Key=file_name, Body=file_content)
        
        return {
            'statusCode': 200,
            'body': json.dumps({'message': 'File uploaded successfully!', 'file_name': file_name})
        }

    except Exception as e:
        return {
            'statusCode': 500,
            'body': json.dumps({'error': str(e)})
        }
````

📸 *Screenshot:* `lambda-code.png`

💡 **Note:** Uploads are done via **Base64 encoding**, so send file content encoded from client/Postman.

---

### 4️⃣ Configure API Gateway

1. Go to **API Gateway → Create API → REST API**
2. Create a new resource: `/upload`
3. Add **POST** method
4. Integration type: **Lambda Function**
5. Choose your Lambda: `S3FileUploadLambda`
6. Deploy API → Stage name: `prod`
7. Copy endpoint URL — e.g.

   ```
   https://xyz123.execute-api.ap-south-1.amazonaws.com/prod/upload
   ```

📸 *Screenshot:* `api-setup.png`

---

### 5️⃣ Test API with Postman

#### 🧾 Step 1: Convert File to Base64

Example in Linux/macOS terminal:

```bash
base64 sample.txt > sample.txt.b64
```

Copy the Base64 content into Postman body 👇

#### 🧠 Step 2: Make POST Request

POST → `https://xyz123.execute-api.ap-south-1.amazonaws.com/prod/upload`

Body → raw JSON (Content-Type: application/json)

```json
{
  "filename": "sample.txt",
  "file": "U29tZSBzYW1wbGUgZmlsZSBjb250ZW50..."
}
```

Response:

```json
{
  "message": "File uploaded successfully!",
  "file_name": "uuid_sample.txt"
}
```

📸 *Screenshot:* `postman-upload.png`

---

### 6️⃣ Verify Upload in S3

1. Go to **AWS Console → S3 → Your bucket → Objects**
2. You’ll see your uploaded file with unique ID prefix
3. Click and download to verify

📸 *Screenshot:* `s3-verify.png`

---

### 7️⃣ Check Logs in CloudWatch

* Go to **CloudWatch → Logs → /aws/lambda/S3FileUploadLambda**
* Verify logs of every upload call

📸 *Screenshot:* `cw-logs.png`

---

## 📂 Repository Structure

```bash
📦 aws-lambda-s3-upload/
├── lambda_function.py
├── screenshots/
│   ├── s3-create.png
│   ├── lambda-create.png
│   ├── lambda-code.png
│   ├── api-setup.png
│   ├── postman-upload.png
│   ├── s3-verify.png
│   └── cw-logs.png
└── README.md
```

---

## 🧠 Key Learnings

* 🪶 Serverless file uploads using Lambda
* 📦 S3 bucket integration for persistent storage
* 🧾 API Gateway for public endpoint access
* 📊 CloudWatch monitoring & error tracing
* ⚙️ Secure uploads via Base64 and IAM role control

---

## 🌟 Future Enhancements

* Add **pre-signed URLs** for direct browser uploads
* Store file metadata in **DynamoDB**
* Trigger another Lambda after upload (Event-driven)
* Compress or resize images automatically
* Integrate with **S3 Object Lambda** for transformations

---

## 📊 Output Summary

| Step            | Description            | Status |
| --------------- | ---------------------- | ------ |
| S3 Bucket       | Created and configured | ✅      |
| Lambda Function | Code and IAM setup     | ✅      |
| API Gateway     | Working REST endpoint  | ✅      |
| File Upload     | Tested successfully    | ✅      |
| CloudWatch Logs | Verified               | ✅      |

---

## 🌐 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge\&logo=linkedin\&logoColor=white)](https://www.linkedin.com/in/sahilshaikh867/)
[![Portfolio](https://img.shields.io/badge/Portfolio-grey?style=for-the-badge\&logo=vercel\&logoColor=white)](https://sahilshaikh867.vercel.app/)

---

## 🎯 Final Outcome

✅ File uploaded to S3 using Lambda
✅ API Gateway integration successful
✅ Logs captured in CloudWatch
✅ Fully serverless file upload pipeline achieved ⚡

> Next Up → AWS Lambda + S3 + DynamoDB Combined Workflow 🔗🔥
> *(Store file → log metadata → trigger notifications!)*
