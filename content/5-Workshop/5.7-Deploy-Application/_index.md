---
title : "Deploy Application"
date : 2026-01-01
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

### Goal

Deploy the CloudCV container on an Amazon EC2 instance.

---

## 1. Overview

CloudCV runs in Docker on Amazon Linux 2023. The report uses a `t3.medium` instance, 20 GB EBS volume, and Elastic IP; these are the project's recorded settings, not universal requirements. EC2 has an IAM role for S3/Bedrock access.

---

## 2. Detailed Practice Content

Complete the following sections in order:

- **5.7.1 Prepare EC2 and Public Access**
- **5.7.2 Build and Run CloudCV**


---

## 3. Expected Result

After completing this chapter, you will have:

- EC2 runs the CloudCV container with a restart policy.
- The `/health` endpoint responds through the Elastic IP on port 8000.
- Data is stored in S3 and AWS permissions come from the IAM role.