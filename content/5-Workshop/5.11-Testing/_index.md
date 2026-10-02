---
title : "Testing"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b> 5.11. </b> "
---

# 5.11. CloudCV API Testing

The API was tested from a client using Postman and curl; Swagger UI is available at `/docs`. The service has no website UI. The following cases are recorded in the report.

## Test Matrix

| Case | Expected/recorded result |
| --- | --- |
| `GET /health` | Check service status |
| `POST /cvs` with a valid PDF | HTTP 201 with CV ID and JSON |
| `POST /cvs` with a valid DOCX | HTTP 201 with CV ID and JSON |
| Protected endpoint, missing/invalid `X-API-Key` | HTTP 401 |
| Upload a non-PDF/DOCX file | HTTP 400 |
| Upload a file larger than 5 MB | HTTP 413 |
| `GET /cvs/{cvId}` for an unknown ID | HTTP 404 |
| Restart EC2/container | Container starts again; previous data remains readable from S3 |

## Data Review

Compare the JSON with the source CV to review contact details, education, experience, skills, languages, and certifications. The report only performs a manual review on a small sample; it does not include a labeled dataset or quantitative accuracy metrics.

## Storage Operations

After creating a CV, use `GET /cvs` and `GET /cvs/{cvId}` to confirm the result can be retrieved. `DELETE /cvs/{cvId}` removes the corresponding CV and JSON from S3; use only disposable test data for deletion tests.

## Test Conclusion

The recorded cases validate the basic API flow, authentication, file checks, and S3 persistence. Extraction accuracy requires further evaluation on a larger CV dataset.


## Parse CV Demo at JobShare

Besides CloudCV, I contributed to the **Parse CV** feature (`POST /v3/resume/cv`) of JobShare's *Resume Parser AI System*. My scope is limited to this feature; the system's other feature groups (Matching, Vector, JD Builder, JD) were not part of my work. The endpoint accepts one or more files (PDF, DOCX...), merges them for parsing, and returns structured JSON.

![Calling the Parse CV endpoint in Swagger UI (personal data redacted)](/images/5-Workshop/demo-parse-cv-jobshare.png)
