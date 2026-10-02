---
title : "Build and Run CloudCV"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

## Install Docker and Get the Source

Connect to EC2 over SSH, install Docker on Amazon Linux 2023, and clone the CloudCV repository from GitHub. Build the image using the project's Dockerfile:

```bash
docker build -t cloudcv .
```

## Start the API

Pass the API key and bucket name through environment variables, then run the container with a restart policy. Variable names must match the source; do not place secrets in the Dockerfile or Git. EC2 obtains S3/Bedrock permissions from its IAM role.

```bash
docker run -d --restart unless-stopped --name cloudcv -p 8000:8000 --env-file <runtime-env-file> cloudcv
```

## Verify the Deployment

- Check container state with `docker ps`.
- Read application output with `docker logs cloudcv`.
- Request `http://<EC2_PUBLIC_IP>:8000/health` from a client.
- Open Swagger UI at `/docs` to inspect the endpoints.

## Expected Result

The container restarts after EC2 reboots; the API responds on port 8000 and can access S3/Bedrock through the IAM role.