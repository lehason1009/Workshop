---
title: "Self-evaluation"
date: 2026-09-27
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

# Self-evaluation

During the 5-week internship (01/08/2026 – 27/09/2026) in the **First Cloud AI Journey** program at Amazon Web Services Vietnam Company Limited, I studied core AWS services and completed the Capstone project **CloudCV**.

## Learning Outcomes (CLO) vs. Results

| CLO | Goal | Result |
| --- | --- | --- |
| CLO1 – Apply technical knowledge | Run an application I wrote on AWS | CloudCV API runs on Amazon EC2 using IAM, VPC/Security Group, EC2, S3, Bedrock, and Budgets |
| CLO2 – Analyze and solve problems | Find causes and fixes on my own when the system fails | Resolved out-of-memory, full disk, API unreachable from the Internet, Bedrock AccessDenied, and invalid LLM JSON issues |
| CLO3 – Communication and reporting | Document work and explain it to others | Weekly worklog, architecture diagrams, API documentation, and the internship report; discussions with mentors in sessions |
| CLO4 – Professional ethics and safety | Follow security practices | No daily root use, root MFA; IAM Role instead of access keys; SSH limited to my IP; API key; sample CVs only |
| CLO5 – Teamwork | Coordinate with mentors and peers | Attended all 7/7 office sessions, asked questions in the FCAJ community; solo project, so limited teamwork experience |
| CLO6 – Technical tools | Become fluent with cloud engineering tools | AWS Management Console, SSH, Docker, Postman, Git/GitHub, Visual Studio Code, draw.io |
| CLO7 – Self-reflection and growth | Reflect and plan next steps | Assessed strengths and weaknesses; planned further study and AWS certifications |

## Strengths

- Read English technical documentation quickly and solved most issues from AWS and Docling docs.
- Prior Python experience made building the API and CV pipeline fast.
- Patient debugging: reading logs and testing hypotheses until the cause is found.
- Security and cost awareness from day one: IAM user and MFA, IAM Role, restricted ports, AWS Budgets, stopping the instance when idle.

## Areas to Improve

- System security knowledge is still introductory.
- Serverless, Load Balancer, Auto Scaling, and ECS known only from docs and labs.
- Manual deployment, no CI/CD yet.
- No user interface and no large dataset to evaluate extraction quality.
- Solo work left little teamwork practice.
- Time management: deployment was crowded into the last two weeks.

## Next Steps (3–6 months)

- Pass AWS Certified Cloud Practitioner, then prepare for AWS Certified Solutions Architect – Associate.
- Upgrade CloudCV: HTTPS, asynchronous processing, monitoring, automated deployment.
- Practice Lambda, Load Balancer, Auto Scaling, and ECS, and add the project to my portfolio.

Long term, I aim to become a backend/cloud engineer who both writes server-side software and operates its cloud infrastructure.
