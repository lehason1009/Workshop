---
title : "Manual Release Process"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.9.1. </b> "
---

## Recorded Release Process

1. Update and verify source code, then push the change to GitHub.
2. Connect to EC2 over SSH.
3. Obtain the source revision to deploy.
4. Rebuild the Docker image using the project Dockerfile.
5. Start the container with runtime configuration and check `/health`.

The container uses a restart policy so it returns with Docker. Keep the API key outside the repository; EC2's IAM role supplies S3/Bedrock access.

## Limitations

These steps are manual. The report does not record a webhook, AWS CodeBuild, ECR, or automated rollback. Before changing the running version, retain the current image or record its commit so it can be restored if needed.

## Expected Result

The source revision and deployed version can be traced, and the new container is healthy before the release is considered complete.