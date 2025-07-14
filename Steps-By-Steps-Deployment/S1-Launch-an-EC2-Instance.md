## 📋 Step-by-Step Guide

### ✅ Step 1: Launch EC2 Instance

1. Go to the [**EC2 Dashboard**](https://console.aws.amazon.com/ec2/)

2. Click **Launch Instance**

3. **Choose an AMI (Amazon Machine Image)**:
   - ✅ Choose **Amazon Linux 2** *(Recommended)*
   - ❗ If using **Ubuntu**, remember to change the **default SSH user** to `ubuntu` instead of `ec2-user` in SSH commands later

4. **Choose an Instance Type**:
   - ✅ Select `t2.micro` (Free Tier eligible)

5. **Configure Instance Settings**:
   - Keep the **default VPC and subnet**
   - ✅ Ensure **Auto-assign Public IP** is **enabled** (so you can connect to the instance)
   - ℹ️ This option may be under "Advanced Details"

6. **Add Storage**:
   - Default 8 GB is sufficient for this project

7. **Add Tags**:
   - Add a name tag for easier identification:
     - Key: `Name`
     - Value: `ImageUploader`

8. **Configure Security Group**:
   - Allow these inbound rules:
     | Type | Protocol | Port | Source |
     |------|----------|------|--------|
     | SSH  | TCP      | 22   | Your IP (recommended) |
     | HTTP | TCP      | 80   | 0.0.0.0/0 (for web access) |

   - 🔒 **Security Note**: Limiting SSH access to "My IP" is safer than opening it to the whole internet

9. **Review and Launch**:
   - Choose or create a **Key Pair** (e.g., `image-uploader-key.pem`)
   - 📥 Download the `.pem` file and **save it securely** — you’ll need this to connect via SSH
   - Launch instance

---

### 🖥️ Connect to EC2 Instance

10. Open your terminal and run this command:

    ```bash
    ssh -i your-key.pem ec2-user@your-ec2-public-ip
    ```

    🔧 **Replace the placeholders**:
    - `your-key.pem`: Replace with the actual filename of your downloaded key (e.g., `image-uploader-key.pem`)
    - `ec2-user`: If you chose Ubuntu instead of Amazon Linux 2, change to `ubuntu`
    - `your-ec2-public-ip`: Replace with the **Public IPv4** address found in the EC2 instance details

    💡 Example:
    ```bash
    ssh -i image-uploader-key.pem ec2-user@18.219.10.101
    ```

11. If you get a permissions error:
    ```bash
    chmod 400 your-key.pem
    ```

---

### ⚙️ Install Required Packages (Amazon Linux 2)

Once connected to your instance:

```bash
sudo yum update -y
sudo yum install -y httpd php unzip aws-cli
```

📌 Note:

If you're using Ubuntu, replace the above with:

```bash
sudo apt update -y
sudo apt install -y apache2 php unzip awscli
```

---

🚀 Start and Enable Apache Web Server
```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

📌 Ubuntu users:
Replace httpd with apache2:
```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

---

✅ Test Web Server
Open your browser and go to:
```arduino
http://your-ec2-public-ip
```

- 🔧 Replace `your-ec2-public-ip` with your actual public IP from the EC2 instance dashboard.
- 🧪 You should see the Apache test page — this confirms your server is up and ready to host your web app.


