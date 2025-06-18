# 🧹💸 **AWS Lambda: Unused EBS Snapshot Cleanup (Cost Optimization Project)** 💸🧹

Automated AWS Lambda function that identifies and deletes **unused, orphaned, or outdated EBS snapshots** to help reduce your AWS bill and keep your infrastructure clean 🧼.

---

## 🚀 Features

✅ **Deletes EBS snapshots** that are:
- 📤 Not attached to any volume  
- 🔌 Taken from volumes not connected to any running EC2 instance  
- 🗑️ Linked to deleted volumes

📊 **Logs every action** into **CloudWatch Logs** for traceability  
🔐 Uses **least privilege IAM role**  
🧠 Written in Python using **boto3**

> 💡 Currently **manually triggered** from the AWS Lambda Console (EventBridge integration optional)

---

## 🛠️ Technologies Used

| Service / Tool     | Purpose                           |
|--------------------|-----------------------------------|
| ☁️ **AWS Lambda**      | Serverless compute environment     |
| 💽 **EBS Snapshots**   | Identified and cleaned up         |
| 🖥️ **EC2 Instances**   | Checked for volume attachments    |
| 🔐 **IAM Roles**       | Secure, scoped access permissions |
| 📦 **boto3 SDK**       | Python AWS SDK to interact with AWS |
| 📊 **CloudWatch Logs** | Audit + Debugging                 |

---

## 🧠 Architecture



🧑‍💻 Manual Trigger (via AWS Lambda Console or CLI)
        |
        ▼
🧠 AWS Lambda Function (Python + boto3 logic)
        |
        ▼
📦 EC2 API Calls:
   ├─ 🖥️ describe_instances
   ├─ 💽 describe_volumes
   ├─ 🧾 describe_snapshots
   └─ ❌ delete_snapshot (if conditions met)
        |
        ▼
📊 CloudWatch Logs:
   └─ 📝 Logs all deletions and errors for audit/debug

