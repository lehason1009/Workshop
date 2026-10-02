---
title : "Prepare EC2 and Public Access"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

## EC2 Configuration

The report deploys CloudCV on Amazon Linux 2023 with a `t3.medium` instance and a 20 GB EBS volume. Create or select a key pair, attach an IAM role with S3/Bedrock permissions, place the instance in a public subnet, and associate an Elastic IP so the address remains stable after restart.

## Security Group Rules

| Port | Source | Purpose |
| --- | --- | --- |
| 22 | Administrator's public IP | SSH |
| 8000 | Testing client | REST API |

Allow SSH only from the administrator's IP. Port 8000 is used by the reported configuration; restrict its source in real deployments when possible.

## Pre-installation Checks

- The instance is running and the Elastic IP is associated.
- The IAM role is attached through an instance profile.
- SSH works from the allowed administrator IP.
- The security group allows API access on port 8000.

## Expected Result

EC2 has a stable public address, AWS access through its IAM role, and the network connectivity needed to install and run the container.