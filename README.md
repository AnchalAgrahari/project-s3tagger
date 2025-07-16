# 🚀 ATS³L — Automated Tagger in S3 via Lambda

## 🧩 Architecture Overview
ATS³L is a fully automated, event-driven system that streamlines the tagging of AWS S3 buckets. Leveraging **AWS Lambda** and **JSON-based configuration**, it eliminates the need for manual tagging by triggering functions the moment a tag definition file is uploaded.

---

## 🏗️ Project Setup & Initial Research
The project began with the creation of an S3 bucket — not through the AWS Console, but **programmatically using Python and Boto3** to ensure repeatability and automation.

### 🔍 References & Learning Sources:
- [Boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html)
- [Step-by-Step Medium Guide](https://medium.com/@techjunction.info/step-by-step-guide-how-to-create-an-s3-bucket-in-aws-84cfb158f405)

These resources helped build foundational knowledge, guiding the initial implementation of bucket creation logic.

---

## 🏷️ Programmatic Tagging
Once the bucket setup was complete, the next objective was to **implement tagging via code**. While tags can be manually added in the AWS Console, this project prioritized scalability and learning by using Python and Boto3.

> ⏱️ **Time to complete tagging logic:** ~1 week (including understanding key-value structure and boto3 syntax)

---

## 🔄 Making Tagging Dynamic with JSON
Manually updating tagging logic per bucket was inefficient. Since AWS tags utilize **key-value pairs**, it was natural to offload this logic into a structured **JSON file**.

### Step 3: Creating an Event-Driven Lambda
- Lambda Name: `ats3l-automated-tagger-in-s3-via-lambda`
- **Trigger**: S3 `putObject` event
- **Purpose**: Detect new JSON uploads and initiate the tagging workflow

---

## 📤 Uploading the Tagging Configuration (JSON)
Before integrating JSON, time was invested in mastering:
- JSON syntax & formatting
- Python JSON parsing (`json.loads()`)
- Reusable tag structure design

Once the JSON file was finalized, the Lambda handler was enhanced to read, interpret, and apply the tags dynamically.

---

## 🧠 Lambda Handler — Core Logic
The handler performs the following sequence:
1. Automatically triggered by new JSON upload to S3
2. Reads the JSON file from S3
3. Parses tag data
4. Uses `put_bucket_tagging()` to apply tags to the S3 bucket

> 💡 The logic is dynamic, event-driven, and fully autonomous.

---

## 🔐 IAM Role & Permissions
To enable proper functionality, the Lambda execution role was assigned:
- `AmazonS3FullAccess`

This allowed it to:
- Read the uploaded JSON file
- Apply tags via Boto3

After deployment, re-uploading the JSON file triggered the function and updated the bucket's tags (visible under **Properties > Tags**).

---

## ⚙️ How It Works — Under the Hood
The system combines **serverless architecture** with **event-driven automation**:

### 🧬 Flow Diagram:
1. 📨 JSON file uploaded to S3
2. 🚀 Lambda function auto-triggered
3. 📖 Reads and parses the file
4. 🏷️ Tags applied programmatically to the bucket

No manual intervention is needed post-deployment — making the solution scalable and future-ready.

---

## 🚧 Key Challenges & Learnings
### 🐍 Python + Boto3
- Lack of experience in Python initially slowed development
- Gained hands-on practice with Boto3 functions (`put_bucket_tagging`, `get_object`, etc.)

### 🔒 IAM Permissions
- Struggled with access issues early on
- Solved by analyzing CloudWatch logs and refining policies

### 📊 CloudWatch Debugging
- Crucial for identifying permission errors and handler failures
- Became essential in the development feedback loop

### 🔁 JSON Re-Uploads
- Realized that to update tags, the same JSON file must be deleted and re-uploaded
- Potential area for future optimization

---

## 🏁 Final Thoughts
This open-source initiative provided in-depth exposure to:
- AWS S3
- Lambda Functions
- IAM Role Configurations
- JSON Data Structures
- Serverless & Event-Driven Design Principles

> 🌟 **ATS³L** represents a simple but powerful automation pipeline — translating uploaded tag configurations into real-time changes with zero manual steps.

---

## ✅ Status: LIVE & DEPLOYABLE
ATS³L is successfully deployed and operational. It serves as both a functional tool and a foundational learning experience in cloud automation. Perfect for anyone exploring **AWS infrastructure as code**, **Lambda automation**, or **S3 management workflows**.

> 🔁 Just upload your tag-config JSON. The rest is magic. ✨
