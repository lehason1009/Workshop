---
title : "Inspect Docker Logs and AWS Budgets"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.10.1. </b> "
---

# Inspect Docker Logs and AWS Budgets

## Application Logs

CloudCV runs in a container on EC2. Use these commands to inspect its state and troubleshoot:

```bash
docker ps
docker logs --tail 100 cloudcv
```

Do not write API keys, full CVs, or personal data to logs. The report does not record log forwarding to CloudWatch; centralized logging requires additional configuration and access controls.

## Cost Alerts

AWS Budgets is configured to send email alerts when charges occur. Check the budget and Billing regularly; a budget alerts but does not stop resources automatically. Stop EC2 when unused to reduce compute charges, but note that EBS and Elastic IP may still incur costs.

## CloudWatch Scope

CloudWatch was covered in the training program, but the report does not describe a CloudWatch log group or alarm for CloudCV. Do not assume the legacy ECS/CPU-alarm configuration applies.

## Expected Result

You can inspect container logs and receive cost alerts, and understand that centralized CloudWatch monitoring needs separate configuration.