## ✅ How to Test If Your Upload Website Is Working

---

### ✅ 1. Visit the Upload Page

Open a browser and navigate to:

> You can find your EC2 Public IP or Public DNS in the AWS EC2 Dashboard.

---

### ✅ 2. Try Uploading a File

- On the page, click **Choose File**
- Select an image (e.g., `.jpg`, `.png`)
- Click **Upload**

---

### ✅ 3. Check for Success Message or Image Preview

If working correctly, your `upload.php` should:

- ✅ Display a success message
- 🖼️ Optionally show an image preview like this:

```html
<img src='https://your-s3-bucket.s3.amazonaws.com/filename.jpg' />
```

---

### ✅ 4. Verify Upload in S3

1. Go to the [**S3 Dashboard**](https://s3.console.aws.amazon.com/s3/)
2. Open your **S3 bucket**
3. Look for the uploaded file in the **object list**

✅ If the file is there — **upload worked!**

---

### ✅ 5. Common Troubleshooting

#### 🚫 Nothing happens or shows an error
- Check `upload.php` for syntax or logic errors
- Use debugging tools like:
  ```php
  echo "Debug message";
  var_dump($variable);
  error_log("Error details here");
  ```

---

#### 🚫 File Not Uploaded to S3

Ensure the following:

- Your **EC2 instance** is using an **IAM role** with at least the `s3:PutObject` permission  
- The **AWS CLI** is installed and functioning on the instance  
- The **S3 bucket name** in your `upload.php` file is accurate and correctly spelled  

---

#### 🚫 Access Denied Error (Image Won’t Display)

If the uploaded image doesn’t load in the browser:

- Make uploaded files **public** (if appropriate for your use case)  
- Or use **pre-signed URLs** via the AWS SDK for secure temporary access  
- Review and adjust your **S3 bucket policy** to allow read access (if needed)

---

### ✅ 6. Test from EC2 Command Line (Optional)

SSH into your EC2 instance:

```bash
ssh -i your-key.pem ec2-user@your-ec2-public-ip
```

Run this command manually to simulate the upload:

```bash
aws s3 cp /tmp/filename.jpg s3://your-bucket-name/
```

> ✅ If this command succeeds, your EC2 instance has the correct IAM permissions to upload to your S3 bucket.
