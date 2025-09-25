# 👥 Linux Task Sheet  

## 🔹 Task 3: User and Group Management  

### 1️⃣ Add users: **raju**, **sham**, and **babubhaiya**; assign passwords to them 🔑  
```bash
sudo useradd raju
sudo passwd raju

sudo useradd sham
sudo passwd sham

sudo useradd babubhaiya
sudo passwd babubhaiya
```
👉 Creates 3 users and sets their passwords.  

---

### 2️⃣ Change the user ID of **raju** to `4002` 🆔  
```bash
sudo usermod -u 4002 raju
```

---

### 3️⃣ Change the user ID of **sham** to `4003` 🆔  
```bash
sudo usermod -u 4003 sham
```

---

### 4️⃣ Create a group named **herapheri** 👨‍👩‍👦  
```bash
sudo groupadd herapheri
```

---

### 5️⃣ Assign a password to the **herapheri** group 🔒  
```bash
sudo gpasswd herapheri
```
👉 This sets a password for the group.  

---

### 6️⃣ Add **raju**, **sham**, and **babubhaiya** to the **herapheri** group ➕  
```bash
sudo usermod -aG herapheri raju
sudo usermod -aG herapheri sham
sudo usermod -aG herapheri babubhaiya
```

---

### 7️⃣ Make **babubhaiya** the admin of the **herapheri** group 👑  
```bash
sudo gpasswd -A babubhaiya herapheri
```
👉 Now **babubhaiya** can manage the group.  

---

### 8️⃣ Remove **sham** from the **herapheri** group ❌  
```bash
sudo gpasswd -d sham herapheri
```

---

✅ **Task 3 Completed!** 🚀  
