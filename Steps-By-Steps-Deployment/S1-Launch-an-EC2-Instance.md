## 📋 Step-by-Step Guide

### ✅ Step 1: Launch EC2 Instance

1. Go to the [**EC2 Dashboard**](https://console.aws.amazon.com/ec2/)
2. Click **Launch Instance**
3. Choose an AMI:
   - **Amazon Linux 2** or **Ubuntu Server**
4. Choose an instance type:
   - Start with **t2.micro** (Free Tier eligible)
5. Configure the instance:
   - Leave default VPC and subnet
   - Enable **Auto-assign Public IP**
6. Add **Storage** (default 8 GB is fine)
7. Add a **Tag** (e.g., Key: `Name`, Value: `ImageUploader`)
8. **Configure Security Group**:
   - Allow:
     - **SSH** on port **22**
     - **HTTP** on port **80**
9. Review and launch:
   - Select an existing key pair or create a new one for SSH access
10. After launching, connect to the instance:
    ```bash
    ssh -i your-key.pem ec2-user@your-ec2-public-ip
    ```

11. Once connected, install required packages:
    ```bash
    sudo yum update -y
    sudo yum install -y httpd php unzip aws-cli
    ```

12. Start and enable Apache:
    ```bash
    sudo systemctl start httpd
    sudo systemctl enable httpd
    ```

13. Confirm your web server is working:
    - Open `http://your-ec2-public-ip` in a browser
