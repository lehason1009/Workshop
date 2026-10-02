---
title: "Week 5 Worklog"
date: 2026-09-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

# Week 5: ELB, Auto Scaling, Docker, and CloudCV deployment

**Period:** 20/09/2026 – 27/09/2026

### Week 5 goals:

* Study Elastic Load Balancer, Auto Scaling, ECS, and Docker basics.
* Deploy CloudCV to AWS.

### Tasks carried out:

| Task | Start date | End date | Source |
| --- | --- | --- | --- |
| Write the Dockerfile (Python 3.12, Docling, CPU PyTorch, pre-downloaded models) | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Create a private S3 bucket and an EC2 IAM Role; request Amazon Bedrock model access | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Launch EC2 t3.medium (Amazon Linux 2023, 20 GB EBS), Security Group ports 22/8000, Elastic IP | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Install Docker, build and run an auto-restarting container; call Bedrock via the Converse API | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Test the API with Postman/curl; track costs with AWS Budgets | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |

### Week 5 results:

* CloudCV runs on EC2 in Docker, stores data in S3, and calls an LLM via Bedrock.
* Test cases 201/400/401/404/413 passed.
* ECS studied conceptually, not yet practiced.
