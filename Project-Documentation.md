# 📸 Project Screenshots & Descriptions

## 1. Created Image Uploader EC2 Instance  
Successfully launched an EC2 instance that serves as the web server for the image uploader application.

![Created Image Uploader Instance](image/1.%20Created-Image-Uploader-Instance.png)

---

## 2. Connected to EC2 Using PuTTY  
Established an SSH connection to the EC2 instance using PuTTY for remote configuration and deployment.  

![Connected to EC2 Using Putty](image/2.%20Connected-To-EC2-Using-Putty.png)

---

## 3. Web Server Is Working  
Installed and verified Apache HTTP server functionality by accessing the EC2 instance's public IP.

![Web Server Is Working](image/3.%20Web-Server-Is-Working.png)

---

## 4. Created Image Uploader S3 Bucket  
Provisioned an S3 bucket that will store uploaded image files securely.  

![Created S3 Bucket](image/4.%20Created-Image-Uploader-Bucket.png)

---

## 5. Created IAM Role for EC2  
Defined an IAM role with permissions to allow EC2 instances to interact with S3.

![Created IAM Role](image/5.%20Created-IAM-Role-For-EC2.png)

---

## 6. Attached IAM Role to EC2 Instance  
Linked the IAM role to the EC2 instance to enable secure access to the S3 bucket without using access keys.  
![Attached IAM Role to EC2](image/6.%20Attached-IAM-Role-For-EC2-To-My-S3-Bucket.png)

---

## 7. Tested EC2 Access to S3 Bucket  
Verified that the EC2 instance can upload to and retrieve from the configured S3 bucket using AWS CLI.  

![Tested EC2 Access](image/7.%20Tested-EC2-Access-To-S3-Bucket.png)

---

## 8. Uploaded PHP and HTML Files Using WinSCP & PuTTY  
Deployed application files (PHP & HTML) to the EC2 server via WinSCP and PuTTY.  

![Uploaded Files](image/8.%20Uploaded-php-and-html-file-using-winscp-and-putty.png)

---

## 9. Created CloudWatch Logging  
Set up CloudWatch for real-time monitoring and logging of application activity and errors.  

![CloudWatch Logging](image/9.%20Created-Cloudwatch-Logging.png)

---

## 10. Tested Image Uploader Web App  
Launched the application in a browser and tested the file upload interface.  

![Tested Web App](image/10.%20Tested-Image-Uploader-Web-App.png)

---

## 11. Uploaded Successfully in the Web App  
Successfully uploaded an image through the front-end and received a confirmation message.  

![Upload Success](image/11.%20Uploaded-Successfully-in-the-Web-App.png)

---

## 12. Verified Upload in the S3 Bucket  
Confirmed that the uploaded image is stored in the specified S3 bucket.  

![Verified in S3](image/12.%20Successfully-Verified-Upload-in-the-S3-Bucket.png)

---

# ⚙️ Optional: Load Balancer & Auto Scaling Setup

## 13. Created Launch Template  
Defined a launch template to standardize EC2 configurations for auto scaling.  

![Launch Template](image/13.%20Created-Launch-Template.png)

---

## 14. Created Auto Scaling Group  
Set up an Auto Scaling Group (ASG) to manage EC2 instances based on load or health.  

![Auto Scaling Group](image/14.%20Created%20Auto-Scaling%20Group.png)

---

## 15. Created Load Balancer for EC2  
Deployed an Application Load Balancer (ALB) to distribute traffic evenly across instances.  

![Load Balancer](image/15.%20Created-Load-Balancer-for-EC2.png)

---

## 16. Created Target Group  
Defined a target group containing EC2 instances that the ALB routes traffic to.  

![Target Group](image/16.%20Created-Target-Group.png)

---

## 17. Attached Target Group to Auto Scaling Group  
Connected the target group with the ASG to automatically manage traffic to new instances.  

![Attached Target Group](image/17.%20Attached-Target-Group-to-Auto-Scaling-Group.png)

---

## 18. Auto Scaling Functioning  
Validated the auto scaling functionality by observing EC2 instances scale based on traffic or health checks.  
![Auto Scaling Works](image/18.%20Autoscaling-Functioning.png)
