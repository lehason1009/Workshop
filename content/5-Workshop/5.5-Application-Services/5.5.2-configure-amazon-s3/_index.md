---
title : "Configure Amazon S3"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

## Configure Amazon S3

CloudCV uses Amazon S3 to store source CV files and JSON results. The bucket remains private; the application accesses it through the EC2 IAM role.

---

## Create an S3 Bucket

Create a bucket in a Region appropriate for EC2 and choose a globally unique name. Keep **Block Public Access** enabled; CV data must not be public.

| Property | Value |
|----------|-------|
| Bucket name | *your-bucket-name* |
| AWS Region | Same Region intended for the application |
| Object Ownership | ACLs disabled |
| Block Public Access | Enabled |

After reviewing the configuration, choose **Create bucket**.

## Stored Data

The API stores the uploaded CV and its analyzed JSON in the bucket. Each CV is referenced by its CV ID so list, read, and delete endpoints can operate on the corresponding objects. Exact key/prefix naming is defined by the project source.

## Verify Access

Attach an appropriate IAM role to EC2 and confirm that the application can write, read, list, and delete objects in the intended bucket. Do not grant public access or place static access keys on the server.

---

## Expected Result

After completing this section, you will have:

- A private bucket for source CVs and JSON results.
- EC2 can access the intended bucket with its granted IAM permissions.