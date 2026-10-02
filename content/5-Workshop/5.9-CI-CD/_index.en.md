---
title : "Source Control and Manual Release"
date : 2026-01-01
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

### Goal

Describe how CloudCV source is managed on GitHub and deployed manually to EC2.

---

## 1. Overview

GitHub is used for source control; the report does not implement AWS CodeBuild or a CI/CD pipeline. The recorded process is to connect to EC2 over SSH, obtain source code, build the Docker image, and restart the container.

---

## 2. Detailed Practice Content

Complete the following section:

- **5.9.1 Manual Release Process**

---

## 3. Expected Result

After completing this chapter, you will have:

- Code changes are tracked in GitHub.
- The manual deployment process can be repeated on EC2.
- The process is not represented as automated CI/CD.