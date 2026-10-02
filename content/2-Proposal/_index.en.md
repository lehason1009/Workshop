---
title: "Proposal"
date: 2026-08-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# CloudCV

## First Cloud AI Journey – Capstone Project CloudCV

---

# 1. Summary

**CloudCV** is a backend REST API that parses CVs automatically. It accepts PDF or DOCX files, converts them to Markdown with **Docling**, calls a large language model (LLM) on **Amazon Bedrock** to extract information, and returns structured JSON.

The application is written in **FastAPI** and packaged as a **Docker** container running on **Amazon EC2**. Original CVs and JSON results are stored in **Amazon S3**. The instance accesses S3 and Bedrock through a least-privilege **IAM Role**, the network is controlled with **VPC** and **Security Groups**, and **AWS Budgets** sends cost alerts.

The project was carried out over 5 weeks (01/08/2026 – 27/09/2026) in the First Cloud AI Journey program at Amazon Web Services Vietnam Company Limited.

---

# 2. Problem and Solution

## Problem

CVs come in many formats and layouts (single column, two columns, tables...). Reading and entering CV data by hand is slow, and extracting raw text from PDFs often mixes columns together.

## Solution

- **Docling** converts CVs to Markdown while keeping section headings, bullets, and tables.
- **An LLM on Amazon Bedrock** extracts information into a fixed schema. The prompt allows only information present in the CV; missing fields are null or empty lists.
- **Pydantic** validates the result. On a schema error, the app retries once with the error message.
- The architecture stays minimal, built around a single EC2 instance, to understand the core AWS services in depth.

---

# 3. Solution Architecture

![CloudCV overall architecture](/images/2-Proposal/kien-truc-cloudcv.png)

The whole application runs in one Docker container on EC2 with three stages:

1. **API layer (FastAPI):** receives and validates requests.
2. **Docling:** converts the CV to Markdown.
3. **Extraction:** calls the LLM on Bedrock and validates the output with Pydantic.

Both the CV file and the JSON result are written to a private S3 bucket, so no separate database is needed.

![CV parsing request flow](/images/2-Proposal/luong-xu-ly-cv.png)

The API is synchronous: the client uploads a file and receives the result in the same request.

## AWS Services

| AWS service | Role |
| --- | --- |
| Amazon EC2 | Instance running the Docker container with FastAPI and Docling |
| Amazon S3 | Stores original CVs and JSON results (private bucket) |
| Amazon Bedrock | Provides the LLM that extracts CV data into JSON |
| AWS IAM | IAM user instead of root; least-privilege IAM Role for EC2 |
| Amazon VPC, Security Group | Public subnet for the instance; only ports 22 and 8000 open |
| AWS Budgets | Cost alerts |

---

# 4. Technical Implementation

## Endpoints

Except for `/health`, every call must include the `X-API-Key` header; a missing or invalid key returns 401.

| Method | Path | Function |
| --- | --- | --- |
| GET | `/health` | Service health check |
| POST | `/cvs` | Upload a CV (multipart/form-data), parse it, return the CV ID and JSON |
| GET | `/cvs` | List parsed CVs |
| GET | `/cvs/{cvId}` | Retrieve a CV's JSON result |
| DELETE | `/cvs/{cvId}` | Delete the CV file and result from S3 |

## Output JSON Schema

| Field | Type | Meaning |
| --- | --- | --- |
| full_name | string | Candidate's full name |
| email, phone, address | string or null | Contact details |
| summary | string or null | Profile/career objective |
| education | list | School, major, degree, period |
| experience | list | Company, position, period, description |
| skills | list of strings | Professional skills |
| languages | list | Languages and proficiency |
| certifications | list | Certificate, issuer, year |

## Infrastructure

- **EC2:** t3.medium, Amazon Linux 2023, 20 GB EBS, public subnet, Elastic IP.
- **Security Group:** port 22 only for a personal IP, port 8000 for the API.
- **Docker:** Python 3.12 image with Docling, CPU-only PyTorch, and pre-downloaded models; auto-restart policy.
- **EC2 IAM Role:** read/write/delete/list objects in the project bucket only, and InvokeModel on the extraction model only.
- **Bedrock:** called through the boto3 Converse API with temperature 0.

---

# 5. Timeline

| Week | Content | Result |
| --- | --- | --- |
| 1 (01/08 – 14/08) | AWS overview; practice account | Done |
| 2 (15/08 – 28/08) | Core services: EC2, S3, IAM | Done |
| 3 (29/08 – 11/09) | AWS networking: VPC, Subnet, Internet Gateway | Done |
| 4 (12/09 – 19/09) | Lambda, Serverless; CloudWatch, CloudTrail | Done (conceptual) |
| 5 (20/09 – 27/09) | ELB, Auto Scaling, ECS, Docker; Capstone project | Done (except ECS hands-on) |

---

# 6. Risks and Limitations

- Synchronous processing; one instance handles few concurrent requests.
- HTTP only, no HTTPS or domain yet.
- Authentication relies on a single shared key.
- Scanned image CVs need OCR, which is slower and less accurate.
- Extraction quality has only been reviewed manually on a small sample.
- To keep costs low, the instance is stopped when idle and spending is tracked with AWS Budgets.

---

# 7. Future Work

- HTTPS and a domain (Nginx or Application Load Balancer), per-user authentication.
- Asynchronous processing with a queue and background workers.
- Infrastructure as Code (CloudFormation, Terraform) with GitHub Actions.
- Monitoring with Amazon CloudWatch.
- A labeled CV dataset to measure per-field extraction quality.
