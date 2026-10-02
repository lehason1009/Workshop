---
title : "Authenticate Requests and Manage Configuration"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.8.1. </b> "
---

## API Authentication

Every endpoint except `GET /health` requires an `X-API-Key` header. A missing or incorrect key returns HTTP 401. Treat the API key as a credential: provide it only through runtime configuration and never commit it to Git, logs, or the image.

## Environment Variables

The application receives its API key and bucket name through environment variables. Exact variable names depend on the source; inspect the project configuration before running it. AWS credentials do not need to be passed as environment variables because EC2 uses an IAM role.

## Network and HTTPS Scope

The report uses an Elastic IP and port 8000 for API testing; it does not record Route 53, ACM, HTTPS, or an ALB. Do not treat a public HTTP endpoint as a production configuration. A broader deployment should add TLS and restrict access as required.

## Expected Result

API keys are validated, sensitive configuration stays out of source code, and the current network-security scope is understood.