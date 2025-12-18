# 🌐 AWS CLOUDFRONT — DEEP & COMPLETE NOTES

---

## 1️⃣ What EXACTLY is CloudFront? (No marketing BS)

**AWS CloudFront = Global Content Delivery Network (CDN)**

Technically:

> CloudFront is a **globally distributed reverse proxy + caching layer** that sits between users and your origin server.

CloudFront does **3 jobs at once**:

1. Route request to nearest edge
2. Cache content intelligently
3. Secure + accelerate delivery

It is NOT just “fast S3” — that’s beginner thinking.

---

## 2️⃣ Why CloudFront is REQUIRED in real systems

### Problem without CDN:

* Origin server overloaded
* High latency for far users
* DDoS risk
* Costly repeated data transfer

### CloudFront solution:

* Load offloads from origin
* Requests served locally
* Fewer origin hits
* Built-in AWS security stack

**Traditional systems always used cache layers** (Squid, Varnish).
CloudFront is AWS’s managed evolution of that idea.

---

## 3️⃣ Core CloudFront Architecture (VERY IMPORTANT)

### 🔹 A) Edge Locations

* Physical AWS locations worldwide
* NOT same as Regions
* Used only for **caching + delivery**

User request always hits **edge first**, never region directly.

---

### 🔹 B) Regional Edge Caches

* Mid-layer between edge & origin
* Store less-frequently accessed objects
* Reduce origin calls further

Think of it as:

```
User → Edge → Regional Cache → Origin
```

Old wisdom: *multi-level cache beats single cache.*

---

### 🔹 C) Origin

Origin is the **source of truth**.

Supported origins:

* Amazon S3 (most common)
* Application Load Balancer
* EC2 instance
* On-prem server
* Any HTTP/HTTPS endpoint

⚠️ CloudFront does NOT care where origin lives.

---

### 🔹 D) Distribution

A **Distribution** is the full CloudFront configuration:

* Origin
* Cache behavior
* Security
* Domain
* Logging

Without distribution → CloudFront does nothing.

---

## 4️⃣ CloudFront Request Lifecycle (Deep Flow)

### Step-by-step:

1. User requests `https://example.com/logo.png`
2. DNS resolves to **nearest edge**
3. Edge checks cache:

   * HIT → return immediately
   * MISS → go to origin
4. Origin returns object
5. Edge:

   * stores object
   * sets TTL
   * serves user

⚡ Cache hit = milliseconds
🐌 Cache miss = origin latency

---

## 5️⃣ Caching Fundamentals (Heart of CloudFront)

### 🔹 Cache Key (VERY IMPORTANT)

Cache key decides **what makes content unique**.

Cache key can include:

* URL path
* Query strings
* Headers
* Cookies

Bad cache key = no caching = slow + expensive

---

### 🔹 TTL (Time To Live)

Controls how long object stays cached.

Sources of TTL:

1. `Cache-Control` header (origin)
2. `Expires` header
3. CloudFront default TTL

TTL hierarchy:

```
Origin headers > Cache behavior settings
```

Old rule: *Cache aggressively, invalidate smartly.*

---

### 🔹 Cache-Control Headers

Common ones:

* `max-age`
* `no-cache`
* `no-store`
* `public`
* `private`

CloudFront respects **HTTP caching standards** — nothing magical.

---

## 6️⃣ Cache Invalidation (Reality Check)

Invalidation = force remove cached object.

* Used when content changes
* Costs money 💸
* Slower than versioning

Best practice:
👉 **Use versioned filenames**

```
app.v1.js → app.v2.js
```

Traditional wisdom: *Never invalidate what you can version.*

---

## 7️⃣ Origins — Deep Dive

### 🔹 S3 Origin

Two types:

1. **S3 REST endpoint (recommended)**
2. S3 static website endpoint (less secure)

Best practice:

* Block public S3
* Allow access only via CloudFront
* Use **Origin Access Control (OAC)**

---

### 🔹 ALB / EC2 Origin

Used for:

* Dynamic content
* APIs
* Auth-based apps

CloudFront still helps by:

* TCP optimization
* TLS reuse
* Regional caching

---

## 8️⃣ Behaviors (Hidden Power Feature)

Behaviors allow **path-based rules**.

Example:

```
/images/* → S3
/api/* → ALB
```

Each behavior controls:

* Allowed HTTP methods
* Cache policy
* TTL
* Security
* Compression

This is where **architect-level decisions** happen.

---

## 9️⃣ Security in CloudFront (VERY STRONG)

### 🔐 HTTPS & SSL

* Default HTTPS
* Supports custom domain + ACM
* TLS termination at edge

---

### 🔐 Signed URLs & Signed Cookies

Used for:

* Paid content
* Private files
* Limited-time access

URL contains:

* Expiry time
* Signature
* Key ID

Without valid signature → access denied.

---

### 🔐 AWS WAF Integration

Protects against:

* SQL injection
* XSS
* Bots
* DDoS

CloudFront + WAF = frontline defense.

---

### 🔐 Geo Restriction

Allow / deny countries.

Use cases:

* Licensing issues
* Compliance
* Abuse prevention

---

## 🔟 Performance Optimizations

### 🔹 Compression

* Gzip / Brotli
* Happens at edge
* Smaller payload = faster

---

### 🔹 HTTP/2 & HTTP/3

* Multiplexing
* Header compression
* Lower latency

CloudFront auto-handles this.

---

### 🔹 Origin Shield

* Single centralized cache before origin
* Reduces origin load drastically

Used in **high-traffic systems**.

---

## 1️⃣1️⃣ Logging & Monitoring

### 🔍 Access Logs

Stored in:

* S3 bucket

Includes:

* IP
* Cache hit/miss
* Response time
* User agent

---

### 📊 CloudWatch Metrics

* Requests
* Error rates
* Cache hit ratio
* Latency

Engineers watch **CacheHitRate like hawks** 🦅

---

## 1️⃣2️⃣ Pricing (Hard Truth)

You pay for:

* Data transfer out
* HTTP/HTTPS requests
* Invalidation requests

Cache miss = higher bill
Cache hit = efficiency + savings

**Good architecture saves money.**

---

## 1️⃣3️⃣ Common Mistakes (Don’t be that guy)

❌ Putting dynamic content with no cache rules
❌ Using invalidation instead of versioning
❌ Allowing public S3 access
❌ Ignoring cache headers
❌ One behavior for everything

Tradition matters because mistakes repeat.

---

## 1️⃣4️⃣ CloudFront in Real DevOps Projects

Typical stack:

```
User
 ↓
Route53
 ↓
CloudFront
 ↓
ALB / S3
 ↓
EC2 / Containers
```

No CDN = incomplete architecture.

---

## 🔥 Final Golden Summary

> **CloudFront is not about speed alone — it’s about scale, security, cost control, and global reliability.**

---
![Image](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2024/05/15/fig1-comfyui-stable-diffusion-1024x580.png?utm_source=chatgpt.com)

![Image](https://docs.aws.amazon.com/images/AmazonCloudFront/latest/DeveloperGuide/images/regional-edge-caches.png?utm_source=chatgpt.com)

![Image](https://blog.shikisoft.com/images/post_imgs/20200805-cloudfront/cache-expiry.jpg?utm_source=chatgpt.com)

![Image](https://d2908q01vomqb2.cloudfront.net/5b384ce32d8cdef02bc3a139d4cac0a22bb029e8/2023/05/16/Screenshot-2023-05-16-at-20.10.27-1024x798.png?utm_source=chatgpt.com)

![Image](https://kodekloud.com/kk-media/image/upload/v1752860751/notes-assets/images/AWS-Certified-SysOps-Administrator-Associate-CloudFront-Caching-Mechanism-and-Potential-Issues/cloudfront-cache-behavior-diagram.jpg?utm_source=chatgpt.com)
