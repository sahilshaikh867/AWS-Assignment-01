# 🖥️ Linux Task Sheet  

## 🔹 Task 4: Process Management  

### 1️⃣ Terminate a specific process using its PID 🛑  
- First, find the PID of a running process:  
```bash
ps aux | grep <process_name>
```
---
- Then terminate it using kill:
```
kill <PID>
```
---
### To force terminate if normal kill fails:
```
kill -9 <PID>
```
---

## 2️⃣ Create a job and run it in the background ⏳
```
sleep 300 &
```
---

- & runs the command in the background.
---

- Check background jobs:
```
jobs
```

## 3️⃣ Bring the background job back to the foreground 🔙
```
fg %<job_number>
```
--- 

Example:
```
fg %1
```

The background job now runs in the foreground.

--------------------------------------------------------------Created By Sahil Shaikh----------------------------------------------------------------------
