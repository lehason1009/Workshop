---
title : "Prepare Project"
date : 2026-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

## CloudCV Project Foundation

CloudCV is a **FastAPI** REST API. Obtain the project source from its GitHub repository and install dependencies using the project's dependency file; the report does not specify a repository URL or exact install command.

## API Contract

| Method | Path | Purpose |
| --- | --- | --- |
| `GET` | `/health` | Check service health |
| `POST` | `/cvs` | Submit a CV for analysis and return its ID and JSON result |
| `GET` | `/cvs` | List analyzed CVs |
| `GET` | `/cvs/{cvId}` | Retrieve one CV result |
| `DELETE` | `/cvs/{cvId}` | Delete the CV and result stored in S3 |

All endpoints except `/health` require an `X-API-Key` header. CV uploads use `multipart/form-data`; the API accepts PDF/DOCX files up to 5 MB.

## Result Schema

Pydantic validates JSON fields grouped as `full_name`, `email`, `phone`, `address`, `summary`, `education`, `experience`, `skills`, `languages`, and `certifications`. The prompt instructs the model to extract only facts present in the CV, avoid guessing missing values, and normalize dates to year-month. Missing fields use `null` or an empty list as defined by the schema.

## Configuration and Authentication

Provide the API key, bucket name, and required settings through the runtime environment instead of hard-coding them. On EC2, use an IAM role for S3 and Bedrock access; do not store static AWS access keys in the application configuration. Keep API keys and real CV data out of Git.

## Expected Result

Understand the API endpoints, JSON schema, and configuration boundaries before packaging the service.