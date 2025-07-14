## 🔐 Connect to EC2 Instance via PuTTY (Windows)

If you're using **PuTTY** and have a `.pem` key file from AWS, you need to convert it to a `.ppk` file first.

---

### ✅ Step 1: Convert `.pem` to `.ppk`

1. Open **PuTTYgen** (installed with PuTTY).
2. Click **Load**.
3. In the file dialog:
   - Change file type to **All Files (\*.\*)**
   - Select your `image-uploader-key.pem` file
4. Click **Save private key**
5. If prompted, click **Yes** to save without a passphrase
6. Save the file as:  `image-uploader-key.ppk`

---

### ✅ Step 2: Connect via PuTTY

1. Open **PuTTY**
2. In the **Host Name (or IP address)** field, enter your EC2 public DNS:
   ```ruby
   ec2-XX-XXX-XXX-XXX.compute-1.amazonaws.com
   ```
   
3. In the **left panel**, navigate to:
4. Click **Browse**, and select your `image-uploader-key.ppk` file
5. (Optional) To save for future use:
- Go back to the **Session** panel
- Enter a name in **Saved Sessions** (e.g., `ImageUploader`)
- Click **Save**

6. Click **Open** to connect
7. On first connect, click **Yes** to trust the host key

---

### 🟢 If You Successfully Connect

You should see a command prompt like:

```bash
[ec2-user@ip-XXX-XXX-XXX-XXX ~]$
```

