---
title : "Configure Network"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

## EC2 Connectivity

In the report's configuration, EC2 is placed in a public subnet and uses an Elastic IP so clients can reach the API on port `8000`. The subnet needs a route to the internet through an Internet Gateway. The deployed CloudCV architecture does not require a private subnet, NAT Gateway, or ALB.

## Security Group

The EC2 security group uses these inbound rules:

| Protocol/port | Source | Purpose |
| --- | --- | --- |
| TCP 22 | Administrator's IP address | SSH administration |
| TCP 8000 | API clients | FastAPI access |

The report restricts port 22 to the administrator's IP and opens port 8000 for API testing. For a real deployment, restrict API sources as appropriate and add suitable protection. Do not expose SSH to `0.0.0.0/0`.

## Verify Connectivity

- Confirm EC2 is in the intended VPC/public subnet and has its Elastic IP attached.
- Check the internet route and instance state.
- From a client, request `http://<EC2_PUBLIC_IP>:8000/health`.
- If the request fails, inspect the security group, address, and application/container status.

## Expected Result

The instance is reachable over SSH from the allowed IP, and the API responds on port 8000. Obtain actual CIDRs and addresses from the deployment account.