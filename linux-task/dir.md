![Image](https://tecadmin.net/wp-content/uploads/2022/06/linux-filesystem-hierarchy-1200x681.png?utm_source=chatgpt.com)

![Image](https://linuxhandbook.com/content/images/2020/06/linux-directory-structure.png?utm_source=chatgpt.com)

![Image](https://www.linuxfoundation.org/hs-fs/hubfs/Imported_Blog_Media/standard-unix-filesystem-hierarchy-1.png?height=1001\&name=standard-unix-filesystem-hierarchy-1.png\&width=1817\&utm_source=chatgpt.com)

---

# 📁 Linux 19 Directories — FULL NOTES + COMMANDS

Root directory `/` ke andar hi sab kuch hota hai. Linux = tree structure 🌳

---

## 1️⃣ `/` (Root)

* Sabka **baap directory**
* Poora Linux yahin se start hota hai

```bash
ls /
```

---

## 2️⃣ `/bin`

* **Basic commands** (for all users)
* System boot hone ke liye required

```bash
ls /bin
# examples: ls, cp, mv, cat
```

---

## 3️⃣ `/sbin`

* **System admin commands**
* Mostly root use karta hai

```bash
ls /sbin
# examples: useradd, reboot, fsck
```

---

## 4️⃣ `/boot`

* System boot files
* Kernel + GRUB

```bash
ls /boot
```

⚠️ Touch bhi mat karna bina reason

---

## 5️⃣ `/dev`

* **Devices as files**
* Hard disk, USB, terminals

```bash
ls /dev
```

Example:

* `/dev/sda`
* `/dev/null`

---

## 6️⃣ `/etc`

* **Configuration files**
* Sab services ka dimaag yahin hota hai

```bash
ls /etc
```

Examples:

* `/etc/passwd`
* `/etc/shadow`
* `/etc/ssh/sshd_config`

---

## 7️⃣ `/home`

* Normal users ka ghar 🏠

```bash
ls /home
```

Example:

```
/home/sahil
```

---

## 8️⃣ `/root`

* Root user ka home
* `/home/root` ❌ (aisa kuch nahi)

```bash
ls /root
```

---

## 9️⃣ `/lib`

* Shared libraries for `/bin` & `/sbin`

```bash
ls /lib
```

Without this → commands fail 💀

---

## 🔟 `/lib64`

* 64-bit system libraries

```bash
ls /lib64
```

---

## 1️⃣1️⃣ `/usr`

* User system resources
* Applications, binaries, libraries

```bash
ls /usr
```

Important subdirs:

* `/usr/bin`
* `/usr/sbin`
* `/usr/lib`

---

## 1️⃣2️⃣ `/var`

* **Variable data**
* Logs, cache, mail, spool

```bash
ls /var
```

🔥 Most important:

```bash
ls /var/log
```

---

## 1️⃣3️⃣ `/tmp`

* Temporary files
* Reboot ke baad clean 🧹

```bash
ls /tmp
```

Anyone can write here:

```bash
touch /tmp/testfile
```

---

## 1️⃣4️⃣ `/proc`

* Virtual filesystem
* Running processes ka data

```bash
ls /proc
```

Example:

```bash
cat /proc/cpuinfo
```

---

## 1️⃣5️⃣ `/sys`

* Kernel & hardware info
* `/proc` ka modern cousin

```bash
ls /sys
```

---

## 1️⃣6️⃣ `/run`

* Runtime data
* PID files, sockets

```bash
ls /run
```

---

## 1️⃣7️⃣ `/mnt`

* Temporary mount point

```bash
mount /dev/sdb1 /mnt
```

---

## 1️⃣8️⃣ `/media`

* Auto-mounted devices
* USB, CD/DVD

```bash
ls /media
```

---

## 1️⃣9️⃣ `/opt`

* Optional / third-party software

```bash
ls /opt
```

Example:

* `/opt/tomcat`
* `/opt/google`

---

# 🧠 One-Line Memory Hack

```
/bin  → commands
/etc  → configs
/var  → logs
/home → users
/dev  → devices
```

Old-school admins isi rule pe jeete hain 😏

---

# 🔥 Exam / Interview Gold

* ❓ Logs kaha hote hain? → `/var/log`
* ❓ Users ka data? → `/home`
* ❓ Config files? → `/etc`
* ❓ Kernel info? → `/proc`, `/sys`
* ❓ Temp files? → `/tmp`

---

## 🧪 Practice Task (kar ke dikha 💪)

1. `/var/log` ke 5 files list kar
2. `/tmp` me file bana ke delete kar
3. `/etc/passwd` ka format samjha
4. `/proc/cpuinfo` read kar

---
