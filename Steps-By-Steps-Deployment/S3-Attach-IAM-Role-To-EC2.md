### ✅ Step 3: Attach IAM Role to EC2

1. Go to the [**IAM Console**](https://console.aws.amazon.com/iam/)
2. Click **Roles** → **Create role**
3. Select **AWS service** > **EC2**
4. Click **Next** and attach the **AmazonS3FullAccess** policy *(for testing only; use a scoped policy in production)*
5. Name your role (e.g., `EC2S3AccessRole`)
6. Create and attach the role:
   - Go to **EC2 Dashboard**
   - Select your instance → Actions → Security → Modify IAM Role
   - Attach the role you just created

7. Test access from EC2:
    ```bash
    aws s3 ls s3://my-upload-bucket
    ```

---
