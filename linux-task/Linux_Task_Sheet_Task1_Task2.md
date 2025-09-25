# 🖥️ Linux Task Sheet  

## 🔹 Task 1: System Information Commands  

### 1️⃣ Display the kernel name 🧑‍💻  
```bash
uname
```
👉 Prints the kernel name (usually Linux).  

---

### 2️⃣ Display the current date and time ⏰  
```bash
date
```
👉 Shows the system date & time.  

---

### 3️⃣ Show your machine name 🖥️  
```bash
hostname
```
👉 Displays the system’s hostname.  

---

### 4️⃣ Display the version and release of the kernel ⚙️  
```bash
uname -r   # Kernel release
uname -v   # Kernel version
```

---

### 5️⃣ Check the size of a directory 📂  
```bash
du -sh /path/to/directory
```
👉 Example:  
```bash
du -sh /home
```
👉 Shows the directory size in human-readable format.  

---

### 6️⃣ Display the OS name 🐧  
```bash
uname -o
```
👉 Prints the OS type (e.g., GNU/Linux).  

---

### 7️⃣ Print the current running shell 🐚  
```bash
echo $SHELL
```

---

### 8️⃣ Check available memory 💾  
```bash
free -h
```
👉 Shows total, used, and free memory.  

---

### 9️⃣ Display the current username 🙋  
```bash
whoami
```

---

## 🔹 Task 2: File and Directory Management  

### 1️⃣ Create a directory with the name `/practice` 📂  
```bash
mkdir /practice
```
👉 Creates a new directory called **practice** in the root.  

---

### 2️⃣ Create a file in the `/practice` directory named `task2.txt` 📄  
```bash
touch /practice/task2.txt
```
👉 Empty file named **task2.txt** is created inside `/practice`.  

---

### 3️⃣ Write 10 lines of data in `task2.txt` using the `vi`/`vim` editor ✍️ (topic: *India*)  
```bash
vi /practice/task2.txt
```
👉 Steps inside `vi`:  
- Press `i` → insert mode  
- Write 10 lines about *India*  
- Press `Esc` → `:wq` to save and quit  

---

### 4️⃣ Copy the first 4 lines of the file and paste them at the end 📑  
Inside `vi`:  
```vim
:1,4y   # yank (copy) lines 1 to 4
:$p     # paste them at the end of file
```

---

### 5️⃣ Find the line number where the word *India* appears 🔎  
Inside `vi`:  
```vim
:/India
```
OR in shell:  
```bash
grep -n "India" /practice/task2.txt
```

---

### 6️⃣ Save the file without quitting the editor 💾  
Inside `vi`:  
```vim
:w
```

---

### 7️⃣ Replace the word *India* with *Bharat* 🔄  
Inside `vi`:  
```vim
:%s/India/Bharat/g
```
👉 Replaces all occurrences globally.  

---

### 8️⃣ Save the file without using `wq` ✅  
Inside `vi`:  
```vim
:x
```
OR simply press `Shift + ZZ`.  

---

### 9️⃣ Copy the `task2.txt` file to `/task3.txt` without using the `cp` command 📤  
```bash
cat /practice/task2.txt > /task3.txt
```
👉 Copies content by redirecting output instead of using `cp`.  

---

✅ **Task 1 & Task 2 Completed!** 🚀
