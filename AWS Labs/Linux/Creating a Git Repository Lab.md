# AWS Lab: Configure an IAM Role for EC2 Instances

## Overview

In this lab, you will learn how to configure an IAM role for EC2 instances that allows them to access an S3 bucket. This is essential for granting permissions without hardcoding credentials into applications or instances.

---

## Customer Scenario

You are working on a project that requires your EC2 instances to read and write files to an S3 bucket. For security and best practices, instead of embedding AWS credentials in your application, you will use IAM roles to provide temporary security credentials.

---

## Task 1: Create an S3 Bucket

### Step 1: Access the AWS Management Console

1. Open the AWS Management Console and log in to your account.
2. Navigate to the S3 service.

### Step 2: Create a New Bucket

1. Click on **Create bucket**.
2. In the **Bucket name** field, enter a unique name (e.g., `my-app-bucket`).
3. Select the appropriate AWS Region.
4. Leave the rest of the options as default and click **Create bucket**.

### Step 3: Verify Bucket Creation

- After the bucket is created, ensure it appears in your S3 bucket list.

---

## Task 2: Create an IAM Role

### Step 1: Access IAM Management

1. In the AWS Management Console, navigate to the **IAM** service.

### Step 2: Create a Role

1. Click on **Roles** in the left navigation panel.
2. Click on **Create role**.

### Step 3: Select Trusted Entity

1. Select **AWS service**.
2. Choose **EC2** as the use case and click **Next: Permissions**.

### Step 4: Attach Permissions Policy

1. In the permissions policy page, search for `AmazonS3FullAccess` or create a custom policy that grants the necessary S3 permissions.
2. Select the policy and click **Next: Tags**.
3. Optionally, add tags and click **Next: Review**.

### Step 5: Review and Create the Role

1. Enter a name for the role (e.g., `EC2S3AccessRole`).
2. Review the details and click on **Create role**.

---

## Task 3: Launch an EC2 Instance with the IAM Role

### Step 1: Launch an EC2 Instance

1. Navigate to the **EC2** service in the AWS Management Console.
2. Click on **Launch Instance**.

### Step 2: Choose Instance Type

1. Select an Amazon Machine Image (AMI) (e.g., Amazon Linux).
2. Choose an instance type (e.g., t2.micro) and click on **Next: Configure Instance Details**.

### Step 3: Configure the Instance

1. In the **IAM role** dropdown, select the IAM role you created earlier (e.g., `EC2S3AccessRole`).
2. Configure additional parameters as needed and click **Next: Add Storage**.

### Step 4: Review and Launch

1. Review your instance settings and click **Launch**.
2. Select an existing key pair or create a new one, then click on **Launch Instances**.

---

## Task 4: Test S3 Access from EC2 Instance

### Step 1: Connect to the EC2 Instance

1. Once the instance is running, connect to it using SSH.
   ```bash
   ssh -i "your-key.pem" ec2-user@your-instance-public-ip
   ```

### Step 2: Install AWS CLI (if not installed)

If the AWS CLI is not installed, run the following commands:
```bash
sudo yum install -y aws-cli
```

### Step 3: Test S3 Access

Run the following command to list the contents of your S3 bucket:
```bash
aws s3 ls s3://my-app-bucket
```

---

## Conclusions

- **IAM Roles:** IAM Roles allow for managed security credentials that are automatically rotated, improving security and reducing the risk of credential leaks.
- **S3 Buckets:** S3 provides scalable object storage and is often used for backup, archiving, and analysis of large data sets.
- **Best Practices:** Using roles reduces the need for hardcoded credentials, making applications more secure and easier to manage.


You can copy this text into a file with the `.md` extension and upload it to your GitHub repository.
