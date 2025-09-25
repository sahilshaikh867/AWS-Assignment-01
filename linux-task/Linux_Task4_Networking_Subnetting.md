# 🌐 Linux Task Sheet  

## 🔹 Task 4: Networking & Subnetting Task  

### 🔸 IP Range

- 192.168.0.0/17 to 192.168.0.0/23

---

### 1️⃣ Calculate the total number of networks 🧮
- `/17` to `/23` means we are **borrowing 6 bits** (23-17).  
- Total networks = `2^(23-17) = 64`  

---

### 2️⃣ Determine the number of hosts available per subnet 🏠
- Number of host bits = `32 - 23 = 9`  
- Hosts per subnet = `2^9 - 2 = 510`  

---

### 3️⃣ List the subnet ranges for each subnet 📋
| Subnet # | Network Range          |
|-----------|----------------------|
| 1         | 192.168.0.0 - 192.168.1.255 |
| 2         | 192.168.2.0 - 192.168.3.255 |
| 3         | 192.168.4.0 - 192.168.5.255 |
| …         | …                    |
| 64        | 192.168.126.0 - 192.168.127.255 |

👉 Each `/23` subnet has 510 usable hosts.  

---

--------------------------------------------------------------Created By Sahil Shaikh----------------------------------------------------------------------
