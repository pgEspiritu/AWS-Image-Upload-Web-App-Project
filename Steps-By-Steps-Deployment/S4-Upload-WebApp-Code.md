### ✅ Step 4: Upload Web App Code

1. On your local machine or inside EC2, create the following two files:

#### `upload.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Image Upload Portal</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to right, #4facfe, #00f2fe);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .upload-container {
      background: #fff;
      padding: 30px 40px;
      border-radius: 12px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
      text-align: center;
      width: 400px;
    }

    .upload-container h2 {
      margin-bottom: 20px;
      color: #333;
    }

    input[type="file"] {
      margin: 15px 0;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }

    input[type="submit"] {
      background-color: #4facfe;
      border: none;
      color: white;
      padding: 10px 25px;
      font-size: 16px;
      cursor: pointer;
      border-radius: 5px;
      transition: background 0.3s ease;
    }

    input[type="submit"]:hover {
      background-color: #00c3ff;
    }

    .footer {
      margin-top: 15px;
      font-size: 12px;
      color: #888;
    }

    @media (max-width: 500px) {
      .upload-container {
        width: 90%;
        padding: 20px;
      }
    }
  </style>
</head>
<body>

  <div class="upload-container">
    <h2>📤 Upload an Image</h2>
    <form action="upload.php" method="post" enctype="multipart/form-data">
      <input type="file" name="file" accept="image/*" required />
      <input type="submit" value="Upload" />
    </form>
    <div class="footer">
      Images will be uploaded securely to AWS S3.
    </div>
  </div>

</body>
</html>
```
---

#### `upload.php`
```php
<?php
if ($_SERVER['REQUEST_METHOD'] == 'POST' && isset($_FILES['file'])) {
    $file = $_FILES["file"]["tmp_name"];
    $name = basename($_FILES["file"]["name"]);
    $bucket = "my-image-uploader-bucket-project"; // replace with your bucket name

    // Move file to temp
    move_uploaded_file($file, "/tmp/" . $name);

    // Upload to S3
    $cmd = "aws s3 cp /tmp/{$name} s3://{$bucket}/{$name}";
    exec($cmd, $output, $status);

    if ($status === 0) {
        echo "✅ Uploaded successfully to S3.<br>";
        echo "<img src='https://{$bucket}.s3.amazonaws.com/{$name}' style='max-width:400px;' />";
    } else {
        echo "❌ Upload failed.";
    }
}
?>
```

---

2. Move these files to your EC2 instance:
```bash
scp -i your-key.pem upload.* ec2-user@your-ec2-ip:/tmp/
ssh -i your-key.pem ec2-user@your-ec2-ip
sudo mv /tmp/upload.* /var/www/html/
```

or for Microsoft user

### ✅ Using WinSCP (GUI — easiest)

1. Open **WinSCP**.
2. Connect to your EC2 instance using the following settings:
   - **Protocol**: `SFTP`
   - **Host**: `ec2-3-136-108-107.us-east-2.compute.amazonaws.com`
       > change this with you public DNS of your EC2
   - **Username**: `ec2-user` (or `ubuntu`, depending on your AMI)
   - **Private Key File**: Use your `.ppk` file

3. Once connected, on the **right panel**, upload your files (e.g., upload.html, upload.php) to: `/home/ec2-user/`
> This folder is owned by your EC2 user and writable.

4. Open PuTTY and SSH into your EC2 instance.
   Move the files to /var/www/html/ using sudo:
   ```bash
   sudo mv /home/ec2-user/upload.* /var/www/html/
   ```
   > ✅ Now your files are in the web server folder with the correct permissions.
