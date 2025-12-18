# 🔧 HANDS-ON: CloudFront + S3 (STEP-BY-STEP)

> Goal:
> **Private S3 bucket → CloudFront → Public Website (Secure + Fast)**

---

## 🧱 Architecture (samajh le pehle)

```
User
 ↓
CloudFront (CDN)
 ↓
Private S3 Bucket (Origin)
```

S3 **public nahi hoga** ❌
CloudFront ke through hi access milega ✅
Ye industry standard hai.

---

## STEP 1️⃣: Create S3 Bucket (Correct Way)

### 1. Open **S3 → Create bucket**

* Bucket name: `my-cloudfront-demo-123`
* Region: any (CloudFront is global)

### 2. Settings

* ❌ Disable public access → **KEEP BLOCKED**
* Bucket versioning: optional (recommended ON)

### 3. Create bucket

💡 **Golden rule:**

> S3 should never be public when CloudFront is in front.

---

## STEP 2️⃣: Upload Static Website Files

Upload:

* `index.html`
* `style.css`
* `script.js`
* any image

Example `index.html`:

```html
<!DOCTYPE html>
<html>
<head>
  <title>CloudFront Demo</title>
</head>
<body>
  <h1>Hello from CloudFront 🚀</h1>
</body>
</html>
```

---

## STEP 3️⃣: Create CloudFront Distribution

### Go to: **CloudFront → Create distribution**

---

### 🔹 Origin Settings

* Origin domain → **Select S3 bucket**
* Origin type → S3
* Origin access → **Origin Access Control (OAC)** ✅
* Create new OAC → Allow CloudFront

🔥 This replaces old OAI (exam favorite).

---

### 🔹 Default Cache Behavior

* Viewer protocol policy → **Redirect HTTP to HTTPS**
* Allowed HTTP methods → GET, HEAD
* Cache policy → `CachingOptimized`
* Compress objects automatically → ✅

---

### 🔹 Settings

* Default root object → `index.html`
* Price class → Use all edge locations
* Logging → Optional (recommended)

Click **Create Distribution**

⏳ Wait ~5–10 minutes (patience = DevOps skill)

---

## STEP 4️⃣: Update S3 Bucket Policy (CRITICAL)

CloudFront will show:

> “Update bucket policy”

Click **Copy Policy** and paste in:
S3 → Permissions → Bucket Policy

Example (auto-generated):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "cloudfront.amazonaws.com"
      },
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-cloudfront-demo-123/*",
      "Condition": {
        "StringEquals": {
          "AWS:SourceArn": "arn:aws:cloudfront::ACCOUNT_ID:distribution/DIST_ID"
        }
      }
    }
  ]
}
```

✅ Only CloudFront can read S3
❌ Public access still blocked

Traditional security principle: **least privilege always wins**.

---

## STEP 5️⃣: Test CloudFront URL

CloudFront gives:

```
https://d123abcxyz.cloudfront.net
```

Open it in browser → 🎉
Your website loads FAST.

Test:

* Open S3 object URL → ❌ Access Denied
* Open CloudFront URL → ✅ Works

Perfect setup.

---

## STEP 6️⃣: Verify Caching (Real Engineer Check)

Open DevTools → Network tab
Reload page

Look for:

* `x-cache: Hit from cloudfront`

First load:

```
Miss from cloudfront
```

Second load:

```
Hit from cloudfront
```

That’s caching working. Chef’s kiss 🤌

---

## STEP 7️⃣: Update Content (Cache Reality)

Change `index.html` text
Upload again to S3

Refresh CloudFront URL →
❌ Old content still there (expected)

Why? Cache.

### Two options:

1️⃣ Version file (best practice)
2️⃣ Invalidate cache (costly)

---

## STEP 8️⃣: Cache Invalidation (Hands-on)

CloudFront → Distribution → Invalidations
Create invalidation:

```
/index.html
```

Wait 1–2 mins → refresh
✅ New content appears

Rule:

> Invalidation is emergency brake, not daily driving.

---

## STEP 9️⃣: (Optional) Custom Domain

* Buy domain in Route53
* Create ACM cert (us-east-1)
* Attach to CloudFront
* Add Route53 A-Alias → CloudFront

Now:

```
https://www.example.com
```

Production ready 💼

---

## 🔥 Final Checklist (Memorize This)

✅ Private S3
✅ CloudFront OAC
✅ HTTPS only
✅ Cache optimized
✅ Versioned files preferred
✅ Invalidation rarely used

---

![Image](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2024/05/15/fig1-comfyui-stable-diffusion-1024x580.png?utm_source=chatgpt.com)

![Image](https://docs.aws.amazon.com/images/whitepapers/latest/build-static-websites-aws/images/s3-web-hosting.png?utm_source=chatgpt.com)

![Image](https://media.amazonwebservices.com/blog/2015/cf_dist_behaviors_1.png?utm_source=chatgpt.com)

![Image](https://blog.mestwin.net/wp-content/uploads/2020/10/cloudfront-form.png?utm_source=chatgpt.com)

