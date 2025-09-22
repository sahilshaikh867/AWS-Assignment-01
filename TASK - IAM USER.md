# 🧑‍💻 AWS Assignment  

## Task 1: IAM  

### 🎯 Objective  
- Enable **MFA (Multi-Factor Authentication)** for an IAM user.  
- Create a new **IAM user with CLI-only access**.  

---

### 🔐 1. Enable MFA for an IAM User  

**Steps:**  
1. Log in to the **AWS Management Console** with root or IAM admin privileges.  
2. Navigate to **IAM → Users**.  
3. Select the IAM user you want to secure.  
4. Go to **Security credentials** tab.  
5. Under **Multi-factor authentication (MFA)**, click **Assign MFA device**.  
6. Choose **Authenticator App** (recommended).  
   - Example apps: Google Authenticator / Authy.  
7. Scan the QR code using your mobile authenticator app.  
8. Enter the 2 consecutive MFA codes shown in the app.  
9. Save settings.  

**Verification:**  
- On next login, AWS will **ask for MFA code** along with username & password.  

---

### 🖥️ 2. Create IAM User with CLI-Only Access  

**Steps:**  
1. Go to **IAM → Users → Add users**.  
2. Enter **username** (e.g., `cli-user`).  
3. Select **Access type: Programmatic access only**.  
   - Do **NOT** enable console access.  
4. Attach permissions:  
   - Option 1: Use an AWS managed policy (e.g., `AmazonEC2FullAccess`).  
   - Option 2: Create a **custom least-privilege policy**.  
5. Complete user creation → Download the **Access Key ID** and **Secret Access Key**.  
6. Configure the user on CLI:  
   ```bash
   aws configure
