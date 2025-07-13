# ATS³L — Automated Tagger in S3 via Lambda

## 🛠️ Architecture Overview
This project automates the process of tagging AWS S3 buckets using Lambda and JSON. The core functionality is event-driven — triggered automatically when a JSON file is uploaded to an S3 bucket. The Lambda function reads, parses, and applies tags programmatically.

---

## 📦 Project Setup & Research

The first step was to create an S3 bucket. While this could be done manually via the AWS Console, I opted for a **programmatic approach using Python and Boto3** for repeatability and scalability.

### References Used:
- [Boto3 Official Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html)
- [Medium Step-by-Step Guide](https://medium.com/@techjunction.info/step-by-step-guide-how-to-create-an-s3-bucket-in-aws-84cfb158f405)

These helped me understand the structure and syntax needed to write the bucket-creation logic, which I implemented successfully.

---

## 🏷️ Tagging the Bucket

Once the bucket was created, I proceeded to **add tags programmatically** using Python. This hands-on approach gave me deeper insight into how AWS tagging works. It took nearly a week to fully grasp the logic and execute the code correctly.

---

## 📄 Making It Dynamic with JSON

Manually writing code for each bucket's tags isn’t scalable. Since AWS tags are **key–value pairs**, I used a **JSON file** to hold all tag data.

### Step 3: Creating the Lambda Function
- I created a Lambda named: `ats3l-automated-tagger-in-s3-via-lambda`
- It is **triggered by S3 events** — when a new JSON file is uploaded, the function runs automatically

---

## ☁️ Uploading the JSON File

Before using JSON, I invested time learning:
- JSON formatting
- Structuring key-value data
- Parsing JSON in Python

Once comfortable, I:
- Wrote a reusable JSON file containing all tag key-value pairs
- Updated the Lambda function to read and apply tags dynamically

Now, simply uploading a JSON file will tag the target S3 bucket.

---

## 🧠 Lambda Handler Logic

The Lambda handler performs the following:
1. Detects the uploaded JSON via S3 event
2. Reads the JSON content
3. Parses the key-value pairs
4. Applies tags to the corresponding bucket using Boto3

---

## 🔐 IAM Permissions & Deployment

For the Lambda function to interact with S3:
- I assigned `AmazonS3FullAccess` policy to the function's IAM role

After deployment, I uploaded the JSON file again. The Lambda triggered and the tags became visible under the bucket’s **Permissions tab**.

---

## ⚙️ Behind the Automation — How It Works

This system is:
- **Event-driven** — triggered automatically when a file is uploaded
- **Serverless** — runs in Lambda without provisioning resources
- **Self-operating** — just upload a JSON file, and it tags the bucket

**Flow Summary:**
1. JSON file is uploaded to S3
2. Lambda is triggered
3. JSON is parsed
4. Tags are applied using `put_bucket_tagging`

---

## ⚠️ Challenges Faced

### Python & Boto3:
- Initially struggled due to limited Python experience
- Learned how to use Boto3 for S3 operations

### IAM Roles:
- Confusing to set up at first
- Took time to figure out exact permissions for reading and tagging

### CloudWatch Logs:
- Difficult to interpret errors early on
- Crucial in identifying permission issues and debugging Lambda execution

### JSON Upload Repetition:
- Discovered that to apply updated tags, I had to **delete and re-upload the same file** — a limitation for future improvement

---

## 🎯 Final Thoughts

This was my first open-source project and a powerful learning experience. I gained hands-on knowledge about:
- AWS S3
- Lambda
- JSON structure
- IAM roles
- Event-driven architecture

Though it was challenging, solving each problem made the project even more rewarding. The final result is a fully automated, reusable tagging solution built with real AWS infrastructure.

> ✅ **ATS³L — Automated Tagger in S3 via Lambda** is now live and deployable.
