---
title: "Sharing and Feedback"
date: 2026-09-27
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

# Sharing and Feedback

## About the Program

What I value most in FCAJ is the learning order: each week adds a layer, and by the final project everything learned has a use. It taught me to approach a cloud problem step by step: clarify requirements, sketch the architecture, choose services, build each part, test, then operate.

Using a single EC2 instance and few services suits a learning project. The system is easy to picture and debug, and it forced me to understand compute, networking, permissions, and storage before moving to more complex models.

## Theory Meets Practice

- **Computer networks:** IPs, ports, and firewalls became concrete when configuring subnets and Security Groups, and when tracing why the API was unreachable.
- **Operating systems:** understanding why a container is killed when memory runs out, and how to inspect resources on a Linux server.
- **Information security:** least privilege applied through an IAM Role instead of stored access keys.
- **Software engineering:** REST API design (methods, status codes, input validation).
- **Information extraction:** an LLM with a constrained schema; even strong models need output validation before production use.

## Suggestions

**For the program:** add a mid-term architecture review. Mentor feedback on the design before implementation would save interns many rewrites.

**For CloudCV:**

- HTTPS and a domain (Nginx or Application Load Balancer); per-user authentication instead of a shared key.
- Asynchronous processing with a queue and background workers.
- Replace manual SSH steps with deployment scripts or Infrastructure as Code (CloudFormation, Terraform) and GitHub Actions.
- Monitoring and alerts with Amazon CloudWatch.
- A labeled CV dataset to measure per-field extraction quality.
