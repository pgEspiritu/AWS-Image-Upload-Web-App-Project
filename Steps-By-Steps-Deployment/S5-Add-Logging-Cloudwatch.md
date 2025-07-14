## ✅ Step 5: Add Logging with CloudWatch

### 🔍 Enable Detailed Monitoring for Your EC2 Instance

1. Go to the **EC2 Dashboard**.
2. Navigate to:  
   `EC2 → Instances → Select Your Instance → Actions → Monitor → Enable Detailed Monitoring`

---

### 📦 Install CloudWatch Agent

```bash
sudo yum install -y amazon-cloudwatch-agent
```

---

### ⚙️ Create Configuration (Optional Quick Config)

```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
```

---

### 🚀 Start the CloudWatch Agent

```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
-a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s
```

---

### 🔔 Optional: Set a CloudWatch Alarm (e.g., CPU > 80%)
1. Go to CloudWatch → Alarms → Create Alarm
2. Choose a metric:
EC2 → `Per-Instance Metrics` → CPUUtilization
3. Set a threshold and notification

---

### 📊 Confirm Logs & Metrics
- View them on the CloudWatch Dashboard
- You should now see real-time monitoring and logs for your EC2 instance
