---
title: "Workshop"
date: 2026-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# CloudCV: A CV Analysis API on AWS

#### Overview

This section documents the development and deployment of **CloudCV**, a backend REST API that accepts CVs in PDF or DOCX format, extracts their content, and returns structured JSON.

The application uses **FastAPI**, **Docling** to convert documents to Markdown, and a language model on **Amazon Bedrock** for information extraction. A Docker container runs on **Amazon EC2**, while **Amazon S3** stores source CVs and JSON results. The EC2 instance uses a least-privilege IAM role to access the bucket and invoke the model. **AWS Budgets** provides cost alerts.

The pages cover project setup, API and data-schema design, S3/IAM/Bedrock integration, Docker packaging, manual deployment to EC2, and API testing. The report does not implement ECS, ECR, a custom domain/HTTPS, or a CI/CD pipeline; pages retained for those legacy sections are reframed to describe the actual scope rather than imply those components were deployed.

#### Content

1. [CloudCV Overview](5.1-Workshop-overview/)
2. [Prerequisite](5.2-Prerequiste/)
3. [Project Foundation and API](5.3-Project-foundation/)
4. [EC2 and Networking](5.4-VPC/)
5. [S3, Bedrock, and IAM](5.5-Application-Services/)
6. [Containerization](5.6-Containerization/)
7. [Deploy to EC2](5.7-Deploy-Application/)
8. [API Security and Configuration](5.8-Domain-and-HTTPS/)
9. [Source Control and Release Process](5.9-CI-CD/)
10. [Logs and Cost Controls](5.10-Monitoring/)
11. [API Testing](5.11-Testing/)
12. [Cleanup](5.12-Cleanup/)