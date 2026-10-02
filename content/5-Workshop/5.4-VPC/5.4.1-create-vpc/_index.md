---
title : "Create VPC"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

## Create VPC

CloudCV uses an AWS VPC to place its EC2 instance in a public subnet. The report does not specify the VPC name or CIDR, so use the VPC selected for your account and record its actual address range instead of copying an example CIDR.

---

## Create a Virtual Private Cloud

In the AWS Console, open **VPC → Your VPCs** and inspect the available VPCs. If you create one, choose an IPv4 CIDR that does not overlap with existing networks, and enable DNS resolution/hostnames if required by the EC2 setup. Record the VPC ID, CIDR, and Region for the following steps.

---

## Verify the VPC

Navigate to:

**AWS Console → VPC → Your VPCs**

Select the VPC you intend to use and verify:

| Property | Expected Value |
|----------|----------------|
| State | Available |
| IPv4 CIDR | Matches the chosen, non-overlapping range |
| DNS Resolution | Enabled |
| DNS Hostnames | Enabled |

Confirm that the VPC has been created successfully before proceeding to the networking configuration.

## Expected Result

After completing this section, you will have:

- A VPC selected for the EC2 instance.
- The actual VPC ID, Region, and CIDR recorded.
- DNS Resolution and DNS Hostnames enabled.
- A VPC ready for configuring subnets and networking resources.