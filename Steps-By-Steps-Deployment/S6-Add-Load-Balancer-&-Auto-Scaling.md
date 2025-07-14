## ⚖️ Step 6 (Optional): Add Load Balancer + Auto Scaling

---

### 🧱 Create a Launch Template

A **Launch Template** defines the configuration for EC2 instances used in Auto Scaling Groups.

#### 🛠️ Steps:

1. Go to the **AWS EC2 Console**.
2. On the left sidebar, click **Launch Templates**.
3. Click **Create launch template**.

#### 📝 Fill in the following fields:

- **Launch template name**: e.g., `image-uploader-template`
- **AMI**: Choose the same Amazon Machine Image (used in your working EC2 instance).
- **Instance type**: Select the same type (e.g., `t2.micro`).
- **Key pair**: Select your existing key pair (e.g., `image-uploader-key`).
- **Network settings**:
  - Choose your existing **security group** (the one allowing HTTP/port 80 and SSH/port 22).
- **IAM instance profile**:
  - Choose the IAM role that grants access to your S3 bucket and CloudWatch.
- **Storage (optional)**:
  - Leave default or customize as needed.
- **Advanced details**:
  - (Optional) Add a **User data script** to automate package installs (e.g., Apache, PHP, CloudWatch agent).

Example `user-data` script:
```bash
#!/bin/bash
yum update -y
yum install -y httpd php unzip aws-cli
systemctl start httpd
systemctl enable httpd
tion Load Balancer`
```

---

## 🔄 Create an Auto Scaling Group (ASG)

An Auto Scaling Group (ASG) automatically manages the number of EC2 instances based on traffic or health checks.

### 🛠️ Steps:

1. Go to the **Auto Scaling Groups** section in the EC2 Console.
2. Click **Create Auto Scaling Group**.
3. Enter the following:

   - **Name**: e.g., `image-uploader-asg`
   - **Launch template**: Select the one you just created

4. **Network**:
   - Choose your existing **VPC**
   - Select **2 or more subnets** across different **Availability Zones** to ensure high availability

5. **Configure group size and scaling policies**:
   - **Minimum capacity**: `1`
   - **Desired capacity**: `2`
   - **Maximum capacity**: `3`

6. *(Optional)* Add health checks or scaling policies based on CPU usage, request count, etc.

7. Click **Create Auto Scaling Group** to finish setup.

---

## 🌐 Create an Application Load Balancer (ALB)

An Application Load Balancer (ALB) distributes incoming HTTP traffic across your EC2 instances in multiple Availability Zones.

### 🛠️ Steps:

1. In the **EC2 Console**, go to:  
   `Load Balancers → Create Load Balancer → Application Load Balancer`

2. **Basic Configuration**:
   - **Name**: `image-uploader-alb`
   - **Scheme**: Internet-facing
   - **IP address type**: IPv4

3. **Listeners**:
   - Keep **HTTP on port 80**

4. **Availability Zones**:
   - Select **at least two Availability Zones**
   - Choose the **subnets** where your ASG instances will be launched

5. Click **Next** to configure security settings (you can skip HTTPS for now).

---

## 🎯 Create a Target Group

A **Target Group** is a set of EC2 instances (or ASGs) that receive traffic from your ALB.

### 🛠️ Steps:

1. Create a new **Target Group**:
   - **Target type**: Instance or Auto Scaling Group
   - **Protocol**: HTTP
   - **Port**: 80
   - **VPC**: Select your existing VPC

2. Register your EC2 instances, **or** leave it empty (if your ASG will automatically attach instances).

3. Click **Create target group**

---

## 🔗 Connect ALB to Auto Scaling Group

1. Go back to your **Auto Scaling Group**.
2. Under the **Load balancing** section, click **Edit**.
3. Attach the **Target Group** you just created.
4. Save changes.

✅ Now, any new EC2 instance launched by your ASG will be automatically registered with the ALB.

---

## 🧪 Test the Setup

1. Go to:  
   `EC2 → Load Balancers → Your ALB → Description tab`

2. Copy the **DNS name** of your ALB.

3. Open it in your browser: `http://your-alb-dns-name`

> You should see your application load — and traffic will be balanced between instances!


