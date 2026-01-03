# AWS S3 Static Website Hosting

## 📌 Overview
This project demonstrates how to host a **public static website** using **Amazon S3**.  
The S3 bucket is configured for **static website hosting**, **public read access**, and serves content directly through the **S3 website endpoint**.

This setup is commonly used for hosting lightweight websites, documentation pages, and landing pages in a cost-effective and scalable way.

---

## 🛠️ AWS Services Used
- **Amazon S3**
- **AWS CLI**

---


---

## 🚀 Step-by-Step Implementation

---

### Step 1: Create an S3 Bucket
1. Open **AWS Management Console**
2. Navigate to **S3**
3. Click **Create bucket**
4. Enter bucket name:Your bucket name'
5. Choose a region (default is fine)

📸 **Image:**  
_Add screenshot showing bucket creation_  


---

### Step 2: Disable Block Public Access
To allow public access for website hosting:

1. Open the bucket
2. Go to **Permissions**
3. Edit **Block public access**
4. Uncheck **Block all public access**
5. Acknowledge the warning and save

📸 **Screenshot:**  
_Add screenshot with arrow pointing to “Block all public access” option_  



---

### Step 3: Enable Static Website Hosting
1. Open the bucket
2. Go to **Properties**
3. Scroll to **Static website hosting**
4. Click **Edit**
5. Enable static website hosting
6. Set:
- Index document: index.html
7. Save changes

📸 **Screenshot:**  
_Add screenshot highlighting static website hosting section_  


---

### Step 4: Configure Bucket Policy for Public Read Access
To allow users to access the website publicly, a bucket policy is added.

Go to:
**Permissions → Bucket Policy**  
Paste the following policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::youbucketarn/*"
    }
  ]
}
```

📸 Screenshot:
## Step 5: Upload index.html to S3

Using AWS CLI from the client host:
```bash
aws s3 cp index.html s3://youbucketname/
```

Verify upload:
```bash
aws s3 ls s3://youbucketname/
```

Expected output:
```diff
index.html
```

## Step 6: Access the Website
Copy the Bucket Website Endpoint from the Static Website Hosting section.

Example:
```arduino
http://datacenter-web-24004.s3-website-us-east-1.amazonaws.com
```
Open it in a browser to view the hosted website.

📸 Screenshot:
