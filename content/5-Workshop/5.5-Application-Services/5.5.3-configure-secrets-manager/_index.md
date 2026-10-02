---
title : "IAM Role for EC2"
date : 2026-01-01
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

## IAM Role for EC2

CloudCV does not use long-lived access keys on the server. Attach an IAM role to EC2 so the application receives temporary credentials and can call AWS services within the granted permissions.

## Required Permissions

| Resource | Permissions in the report |
| --- | --- |
| Project S3 bucket | List the bucket; read, write, and delete objects in that bucket |
| Amazon Bedrock | Invoke the model used for extraction |

Scope the policy to the bucket/object ARN and required model; avoid `*` unless necessary. Do not place access keys in the Docker image, Git, or long-lived environment variables.

## Attach and Verify the Role

Attach the role through the EC2 instance profile, then verify that the application can write/read a test object and invoke the model. For AccessDenied, check the policy, bucket ARN, model ID, and Region.

## Expected Result

EC2 uses temporary credentials from an IAM role with the required S3 and Bedrock permissions, without static AWS access keys.