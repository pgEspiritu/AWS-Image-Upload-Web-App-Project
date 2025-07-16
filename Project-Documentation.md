# 📸 Project Screenshots & Descriptions

## 1. Created Image Uploader EC2 Instance  
Successfully launched an EC2 instance that serves as the web server for the image uploader application.  
![Created Image Uploader Instance](image/1. Created-Image-Uploader-Instance.png)

---

## 2. Connected to EC2 Using PuTTY  
Established an SSH connection to the EC2 instance using PuTTY for remote configuration and deployment.  
![Connected to EC2 Using Putty](image/1. Created-Image-Uploader-Instance.png)

---

## 3. Web Server Is Working  
Installed and verified Apache HTTP server functionality by accessing the EC2 instance's public IP.  
![Web Server Is Working](image/1. Created-Image-Uploader-Instance.png)

---

## 4. Created Image Uploader S3 Bucket  
Provisioned an S3 bucket that will store uploaded image files securely.  
![Created S3 Bucket](image/1. Created-Image-Uploader-Instance.png)

---

## 5. Created IAM Role for EC2  
Defined an IAM role with permissions to allow EC2 instances to interact with S3.  
![Created IAM Role](image/1. Created-Image-Uploader-Instance.png)
---

## 6. Attached IAM Role to EC2 Instance  
Linked the IAM role to the EC2 instance to enable secure access to the S3 bucket without using access keys.  
![Attached IAM Role to EC2](image/1. Created-Image-Uploader-Instance.png)

---

## 7. Tested EC2 Access to S3 Bucket  
Verified that the EC2 instance can upload to and retrieve from the configured S3 bucket using AWS CLI.  
![Tested EC2 Access](image/1. Created-Image-Uploader-Instance.png)

---

## 8. Uploaded PHP and HTML Files Using WinSCP & PuTTY  
Deployed application files (PHP & HTML) to the EC2 server via WinSCP and PuTTY.  
![Uploaded Files](image/1. Created-Image-Uploader-Instance.png)

---

## 9. Created CloudWatch Logging  
Set up CloudWatch for real-time monitoring and logging of application activity and errors.  
![CloudWatch Logging](image/1. Created-Image-Uploader-Instance.png)

---

## 10. Tested Image Uploader Web App  
Launched the application in a browser and tested the file upload interface.  
![Tested Web App](image/1. Created-Image-Uploader-Instance.png)

---

## 11. Uploaded Successfully in the Web App  
Successfully uploaded an image through the front-end and received a confirmation message.  
![Upload Success](image/1. Created-Image-Uploader-Instance.png)

---

## 12. Verified Upload in the S3 Bucket  
Confirmed that the uploaded image is stored in the specified S3 bucket.  
![Verified in S3](image/1. Created-Image-Uploader-Instance.png)

---

# ⚙️ Optional: Load Balancer & Auto Scaling Setup

## 13. Created Launch Template  
Defined a launch template to standardize EC2 configurations for auto scaling.  
![Launch Template](image/1. Created-Image-Uploader-Instance.png)

---

## 14. Created Auto Scaling Group  
Set up an Auto Scaling Group (ASG) to manage EC2 instances based on load or health.  
![Auto Scaling Group](image/1. Created-Image-Uploader-Instance.png)

---

## 15. Created Load Balancer for EC2  
Deployed an Application Load Balancer (ALB) to distribute traffic evenly across instances.  
![Load Balancer](image/1. Created-Image-Uploader-Instance.png)

---

## 16. Created Target Group  
Defined a target group containing EC2 instances that the ALB routes traffic to.  
![Target Group](image/1. Created-Image-Uploader-Instance.png)

---

## 17. Attached Target Group to Auto Scaling Group  
Connected the target group with the ASG to automatically manage traffic to new instances.  
![Attached Target Group](image/1. Created-Image-Uploader-Instance.png)

---

## 18. Auto Scaling Functioning  
Validated the auto scaling functionality by observing EC2 instances scale based on traffic or health checks.  
![Auto Scaling Works](image/1. Created-Image-Uploader-Instance.png)
