---
title : "Integrate Amazon Bedrock"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

## Integrate Amazon Bedrock

CloudCV invokes a language model on Amazon Bedrock to transform CV Markdown into JSON matching the Pydantic schema. The report does not identify a model ID; select a model enabled in the account's Region.

## Model Invocation

The application uses boto3's Converse API. Temperature is set to `0` to reduce randomness. The prompt instructs the model to use only information present in the CV, avoid guessing missing values, and normalize dates to year-month.

## Validate the Response

Convert the model response to JSON and validate it with Pydantic before storing or returning it. If the JSON does not match the schema, the application retries once with the validation error. Invoke Bedrock through the EC2 IAM role; do not embed AWS access keys in source code.

## Expected Result

EC2 can invoke the intended model and the application receives a valid result matching the CloudCV schema.