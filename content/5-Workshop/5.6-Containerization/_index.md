---
title : "Containerization"
date : 2026-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

### Goal

Package the FastAPI application, Docling, and its dependencies into a Docker image for EC2.

---

## 1. Overview

CloudCV uses Python 3.12. The image installs Docling with a CPU-only PyTorch build and preloads the layout-analysis models Docling needs. The report deploys the image directly on EC2 and does not use Amazon ECR.

---

## 2. Detailed Practice Content

Complete the following sections in order:

- **5.6.1 Build Docker Image**
- **5.6.2 Prepare the EC2 Container Runtime**

---

## 3. Expected Result

After completing this chapter, you will have:

- A Docker image containing the API and document-processing dependencies.
- Docling models available when the container starts.
- Runtime settings ready for direct deployment on EC2.