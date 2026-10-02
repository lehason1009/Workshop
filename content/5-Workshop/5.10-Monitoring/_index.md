---
title : "Logs and Cost Controls"
date : 2026-01-01
weight : 10
chapter : false
pre : " <b> 5.10. </b> "
---

### Goal

Inspect container logs and configure AWS cost alerts for CloudCV.

---

## 1. Overview

During operation, use Docker logs on EC2 to inspect startup output and application errors. AWS Budgets sends alerts when the account incurs costs. The report includes CloudWatch training but does not record CloudWatch Logs or alarms configured for CloudCV.

---

## 2. Detailed Practice Content

Complete the following section:

- **5.10.1 Inspect Docker Logs and AWS Budgets**

---

## 3. Expected Result

After completing this chapter, you will have:

- Container logs can be inspected directly on EC2.
- AWS Budgets is used for cost alerts.
- The previous ECS/CloudWatch setup is not confused with the current EC2 architecture.