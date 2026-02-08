# AWS Cloud Cost Optimization — Identifying Stale EBS Snapshots

This project automates the identification and cleanup of stale Amazon EBS snapshots to reduce unnecessary AWS storage costs.

Problem Statement

Over time, EBS snapshots accumulate in AWS accounts—even after their associated EC2 volumes or instances are deleted. These unused snapshots continue to incur storage charges, leading to avoidable cloud costs.

Solution Overview

I implemented an AWS Lambda function in Python that:

Retrieves all EBS snapshots owned by the account (owner='self').

Fetches a list of active EC2 instances (both running and stopped).

For each snapshot, checks whether its associated EBS volume is still attached to any active EC2 instance.

If the snapshot is not associated with any active instance, it is considered stale and is automatically deleted.

This helps keep storage usage minimal and ensures cost-efficient AWS resource management.

Automation Using CloudWatch

To run this process automatically, I configured Amazon CloudWatch Events (EventBridge) as a scheduled trigger for the Lambda function.

The Lambda runs periodically (e.g., once a day or once a week).

This ensures continuous monitoring and cleanup without manual intervention.

The CloudWatch rule invokes the Lambda function based on a cron schedule.
https://github.com/shiva-prasad1503/AWS-Cloud-Cost-Optimization-/blob/main/AWS%20snapshot%20deletion%20automation%20flowchart.png
![AWS Stale EBS Snapshot Architecture](
AWS-Cloud-Cost-Optimization-/AWS snapshot deletion automation flowchart.png)


AWS Services Used

✅ AWS Lambda

✅ Amazon EC2

✅ Amazon EBS

✅ Amazon CloudWatch (EventBridge)

✅ AWS Boto3 (Python SDK)

Use Case

This solution is particularly useful for:

Cloud cost optimization

DevOps automation

FinOps practices

AWS governance and resource management
