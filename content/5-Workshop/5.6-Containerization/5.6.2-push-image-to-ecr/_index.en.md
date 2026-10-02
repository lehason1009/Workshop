---
title : "Prepare the EC2 Container Runtime"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

## Prepare the EC2 Container Runtime

The report deploys directly on EC2, so ECR is not required. After installing Docker on Amazon Linux 2023 and obtaining the source from GitHub, build the image on the instance:

```bash
docker build -t cloudcv .
```

## Runtime Configuration

Pass the API key and bucket name as environment variables when starting the container. Obtain the exact variable names from the source; never commit secret values to Git. EC2 receives S3/Bedrock access through its IAM role, not long-lived access keys.

Example command structure (adjust the port and configuration file to the project):

```bash
docker run -d --restart unless-stopped --name cloudcv -p 8000:8000 --env-file <runtime-env-file> cloudcv
```

## Verify the Container

Confirm the container is running, inspect startup logs, and request `/health` on port 8000. The restart policy brings the container back after Docker or EC2 restarts.

## Expected Result

The image is built and running on EC2; application settings are supplied at startup, while AWS permissions come from the IAM role.