## 🪣 AWS S3 (Simple Storage Service)

S3 = **internet ka godown**. Jo bhi data ho — images, videos, backups, logs, PDFs, app files — sab yahin safe rehta hai.

---

## 🔹 Core Basics (ye yaad rehna hi chahiye)

* **Bucket** → folder jaisa (but globally unique name 😤)
* **Object** → actual file (data + metadata)
* **Key** → file ka path inside bucket
* **Region-based** → bucket ek region me hota hai
* **Durability** → 99.999999999% (11 nines, matlab data marrta nahi 💀)

---

## 🔹 Why S3 is GOAT 🐐

* **Unlimited storage** (space ki tension zero)
* **Pay as you use** (gareeb-friendly 😌)
* **Highly secure** (IAM + Bucket Policy + Encryption)
* **Super scalable** (startup se unicorn tak same service)

Industry fact: *Netflix, Airbnb, Adobe — sab S3 use karte hain*. Old school storage gaya, S3 era chal raha.

---

## 🔹 Common Real-World Use Cases

* Website static hosting (HTML/CSS/JS)
* App images & videos
* Database backups
* Logs storage (CloudWatch → S3)
* DevOps pipelines artifacts (Jenkins, GitHub Actions)

---

## 🔹 Storage Classes (paisa bachane ka funda 💸)

* **Standard** → frequent access
* **IA (Infrequent Access)** → kabhi-kabhi
* **One Zone-IA** → cheap but risky
* **Glacier** → archive (months/years)
* **Glacier Deep Archive** → sabse sasta, slow access

👉 Smart log lifecycle lagao, warna bill dekh ke rona aayega.

---

## 🔹 Security (yahaan log atakte hain)

* **IAM Policies** → user level access
* **Bucket Policy** → bucket level rules
* **ACLs** → old school, mostly avoid
* **Encryption**

  * SSE-S3
  * SSE-KMS (industry fav ⭐)
* **Block Public Access** → ON rakhna by default

Rule of thumb: *Public bucket = career suicide* ☠️

---

## 🔹 S3 + DevOps Combo 🔥

Since tu DevOps track pe hai:

* Jenkins build artifacts → S3
* Terraform → S3 backend (state file)
* CloudFront → S3 static site
* Lambda → S3 trigger (event-driven magic ✨)

Old sysadmin backup mindset + modern cloud scale = S3.

---

## 🔹 Exam / Interview Punchlines

* S3 is **object storage**, not block/file
* Bucket names are **globally unique**
* Data is stored **across multiple AZs**
* Default storage class = **Standard**

---
![Image](https://d2908q01vomqb2.cloudfront.net/e1822db470e60d090affd0956d743cb0e7cdf113/2023/02/17/Arch_Diagram_Replication_Image2.png?utm_source=chatgpt.com)

![Image](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2021/08/02/Fig1-S3-Object.png?utm_source=chatgpt.com)

![Image](https://awsfundamentals.com/_next/image?q=100\&url=%2Fassets%2Finfographics%2Foptimized%2Fs3_dark.webp\&w=3840\&utm_source=chatgpt.com)

![Image](https://kodekloud.com/kk-media/image/upload/v1752869348/notes-assets/images/Amazon-Simple-Storage-Service-Amazon-S3-Storage-Classes/aws-s3-glacier-deep-archive-infographic.jpg?utm_source=chatgpt.com)

