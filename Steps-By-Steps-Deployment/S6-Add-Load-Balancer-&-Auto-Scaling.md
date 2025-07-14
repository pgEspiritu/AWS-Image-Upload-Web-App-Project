## ⚖️ Step 6 (Optional): Add Load Balancer + Auto Scaling

### 🧱 Create a Launch Template

1. Navigate to:  
   `EC2 → Launch Templates → Create`

2. Use the same:
   - AMI
   - Instance type
   - Key pair
   - Security group
   - IAM role

3. (Optional) Add a **user data script** if needed.

---

### 🔄 Create an Auto Scaling Group (ASG)

1. Use your **Launch Template**
2. Set:
   - **Minimum capacity**: 1
   - **Maximum capacity**: 3
   - **Desired capacity**: 2
3. Choose **multiple subnets** (across Availability Zones)

---

### 🌐 Create an Application Load Balancer (ALB)

1. Go to:  
   `EC2 → Load Balancers → Create Load Balancer → Application Load Balancer`

2. Select **at least 2 Availability Zones**
3. Create a **Target Group**:
   - Protocol: HTTP
   - Port: 80
   - Register EC2 instances or the Auto Scaling Group

---

### 🔗 Connect ALB to Auto Scaling Group

1. Attach your **ASG** to the **Target Group**

---

### 🧪 Test the Setup

- Visit the **ALB DNS name** in your browser to verify that traffic is distributed and the app is running.
