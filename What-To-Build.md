## 🌟 What You’ll Build

A **simple image upload web app**, hosted on **Amazon EC2**, storing uploaded files in **Amazon S3**, secured using **IAM roles**, monitored with **CloudWatch**, and (optionally) scaled using **Application Load Balancer (ALB)** and **Auto Scaling Groups (ASG)**.

---

## 🚀 What It Does

- 🌐 Users visit a web interface hosted on EC2  
- 📤 Users upload an image or file  
- 🪣 The file is stored in an S3 bucket  
- ✅ (Optional) A confirmation message or image preview is shown  
- ⚖️ (Optional) Traffic is distributed using ALB with auto-scaling for high availability  

---

## 🧠 Why It’s Awesome

- ✅ It's a practical, real-world app  
- 🛠️ Demonstrates 5–6 core AWS services working in harmony  
- 📦 Easily deployable and shareable on GitHub  
- 📚 Covers infrastructure, security, scaling, and observability  

---

## 🔧 Tech Stack and AWS Services

| Component       | AWS Service        | Purpose                              |
|----------------|--------------------|--------------------------------------|
| Web Server      | EC2                | Host the web application             |
| Storage         | S3                 | Store uploaded files                 |
| Permissions     | IAM                | Secure EC2-to-S3 access              |
| Monitoring      | CloudWatch         | Track usage, uptime, set alarms      |
| Load Balancer   | ALB (optional)     | Distribute incoming traffic          |
| Auto Scaling    | ASG (optional)     | Scale EC2 instances automatically    |

---

## 🖼️ Architecture Diagram

![Diagram](image/Architecture.png)
