# 🪣 AWS S3 Hands-On Guide

## 🧩 Step-by-Step Hands-On (Console)

### 1. Go to S3 Console
👉 [Open AWS S3 Console](https://s3.console.aws.amazon.com/s3)

---

### 2. Create a Bucket
- **Name:** `sahil-learning-bucket` *(must be globally unique)*  
- **Region:** Choose your nearest region (e.g., `ap-south-1`)  
- **Public Access:** Uncheck **“Block all public access”** *(only if you plan to host a static website)*  
- Keep other defaults as they are  
- Click **Create bucket**  

---

### 3. Upload a File
- Open your new bucket  
- Click **Upload** → **Add files** → choose a file (e.g., `notes.txt`)  
- Click **Upload**  

---

### 4. Check Object URL
- After upload, click your object name  
- Copy the **Object URL**  
- If the file is public, open it in your browser to view  

---

### 5. Enable Versioning (optional)
- Go to your bucket → **Properties** tab  
- Scroll to **Versioning** → click **Edit** → **Enable**  
- Upload another file with the same name to see multiple versions appear  

---

### 6. Enable Server-Side Encryption (optional)
- Go to your bucket → **Properties** tab  
- Scroll to **Default encryption** → **Edit**  
- Choose **SSE-S3** (Amazon-managed key) or **SSE-KMS** (your own key)  
- Save changes  

---

✅ **That’s it!**  
You’ve successfully created a bucket, uploaded files, and secured your data with S3.  
Next step: try **integrating S3 with AWS Lambda** for event-driven automation! 🚀
