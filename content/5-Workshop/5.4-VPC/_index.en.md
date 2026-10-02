---
title : "Networking"
date : 2026-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

### Goal

Describe how CloudCV's EC2 instance reaches the internet and how its security group controls inbound traffic.

---

## 1. Overview

CloudCV runs on an EC2 instance in a public subnet so clients can reach the API. An Elastic IP keeps the instance address stable; its security group allows SSH from the administrator's IP and API traffic on port 8000. The report does not specify a CIDR, Region, NAT, or ALB configuration, so the following pages focus on documented choices rather than invented network values.

---

---

## 2. Detailed Practice Content

Refer to these sections:

- **5.4.1 Create VPC**
- **5.4.2 Configure Network**

---

## 3. Expected Result

After completing this chapter, you will have:

- Understand the VPC/public-subnet role in reaching the EC2 instance.
- Understand why SSH access and API traffic need distinct security-group rules.
- Record the actual CIDR, Region, and account-specific rules before deployment.