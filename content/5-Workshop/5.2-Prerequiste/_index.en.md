---
title : "Prerequisite"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

### Goal

Prepare an AWS account, a Python/Docker development environment, and an API client before working with CloudCV.

---

## 1. Tools to Prepare

The report's resources are managed in AWS. Use an account allowed to create EC2, S3, and IAM resources and access Amazon Bedrock; model invocation must be enabled before integration testing.

Please prepare the following software:

- **Python 3.12** and a Python package environment.
- **Docker** to build and run the container.
- **Git** to obtain source code and track changes.
- **Postman** or **curl** for REST API requests; a browser can access Swagger UI.
- A sample PDF or DOCX CV within the API's 5 MB limit.

---

## 2. Steps

**Log in to AWS Console:** Select a Region where your account can use Amazon Bedrock and confirm that the intended model is available there.

**Checkpoint:** Record the Region used for EC2 and Bedrock; configure both consistently.

**Verify Local Tools:** Confirm that Python, Git, and Docker are available.

```bash
python --version
git --version
docker --version
```

**Checkpoint:** All commands should return valid version numbers.

**Prepare AWS access:** Create an AWS budget for cost alerts and request access to the Bedrock model before running the API.

---

## 3. Expected Result

- Python 3.12, Docker, and Git are available.
- The account can create required resources and invoke the Bedrock model.
- An API client and sample CV are ready for testing.