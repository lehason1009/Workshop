+++
title = "Cleanup Resources"
date = 2024-01-01
weight = 12
chapter = false
pre = "<b>5.12. </b>"
+++

# 5.12. CloudCV Resource Cleanup

## Before Deleting

These steps are a cleanup checklist, not a claim that the report's resources have already been deleted. Back up any CVs/results to retain before deleting the bucket; emptying S3 is irreversible without a separate copy.

## Cleanup Order

1. Stop the container and confirm the API is no longer needed.
2. In EC2, terminate the CloudCV instance. Choose how to handle its EBS volume according to your retention needs.
3. Release the Elastic IP after disassociating it; an unattached public address may incur charges.
4. If the data is no longer needed, delete objects in the CloudCV bucket and then delete the bucket.
5. Detach the IAM role from EC2; delete project-specific roles/policies only when no service uses them.
6. Delete the security group, subnet, Internet Gateway, and VPC only if they were created exclusively for CloudCV and have no dependencies.
7. Revoke the API key in use and review IAM permissions to invoke Bedrock.
8. Check Billing/AWS Budgets for remaining billable resources. The budget can be retained to monitor the account.

## Verify

Confirm the EC2 instance is terminated, the Elastic IP is released, the bucket is handled according to the retention decision, and unused IAM permissions are removed. Do not delete shared infrastructure or data that must be retained.