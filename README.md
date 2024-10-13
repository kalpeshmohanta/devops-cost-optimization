# AWS Cloud Cost Optimization - Identifying Stale(unused) Resources

## Identifying Stale EBS Snapshots

In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

### Description

The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

### Requirement

- Add the necessary **IAM policy** to the Lambda function's **role**, granting access to EC2, EBS volumes, and snapshots to interact with AWS services effectively.
- Set up a **CloudWatch Events** rule to **trigger** the Lambda function on a schedule (e.g., daily or weekly) to continuously monitor for stale snapshots.
- Lambda function's **optimization of memory and timeout settings**.
