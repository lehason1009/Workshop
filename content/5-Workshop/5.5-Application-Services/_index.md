---
title : "Application Services"
date : 2026-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

### Goal

Configure the three AWS services central to CloudCV: Bedrock, S3, and IAM.

---

## 1. Overview

CloudCV uses Amazon Bedrock to extract CV data, Amazon S3 to store source CVs and JSON results, and an IAM role attached to EC2 for access to Bedrock and the bucket. The report does not use MongoDB Atlas or AWS Secrets Manager.

---

## 2. Detailed Practice Content

Complete the following sections in order:

- **5.5.1 Integrate Amazon Bedrock**
- **5.5.2 Configure Amazon S3**
- **5.5.3 IAM Role for EC2**

---

## 3. Expected Result

After completing this chapter, you will have:

- Understand Bedrock, S3, and IAM roles in the request flow.
- EC2 permissions are scoped to the required bucket and model.
- Source files and results are stored in a private bucket.