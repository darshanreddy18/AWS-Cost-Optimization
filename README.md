# AWS Cloud Cost Optimization – Identifying Stale EBS Snapshots

## Project Overview
This project uses AWS Lambda and Python (Boto3) to identify stale Amazon EBS snapshots and delete unnecessary snapshots to reduce AWS storage costs.

## AWS Services Used
- AWS Lambda
- Amazon EC2
- Amazon EBS Snapshots
- AWS IAM

## Lambda Implementation Details

1. **Initialize Boto3:** Use the AWS SDK for Python to interact with EC2 resources.
2. **Fetch EBS Snapshots:** Retrieve snapshots owned by the current AWS account.
3. **Fetch EC2 Instances:** Retrieve instances in running and stopped states.
4. **Identify Stale Snapshots:** Check snapshot-related volumes and determine whether they are associated with active EC2 instances.
5. **Delete Snapshots:** Delete snapshots identified as unnecessary to reduce storage costs.
6. **Return Results:** Log the identified and deleted snapshots in Amazon CloudWatch Logs.

## Implementation Workflow

```text
AWS Lambda
    |
    v
Fetch EBS Snapshots
    |
    v
Fetch EC2 Instances
    |
    v
Identify Stale Snapshots
    |
    v
Delete Unnecessary Snapshots
    |
    v
CloudWatch Logs
```

## IAM Permissions
The Lambda execution role requires appropriate permissions, including:
- `ec2:DescribeSnapshots`
- `ec2:DescribeInstances`
- `ec2:DescribeVolumes`
- `ec2:DeleteSnapshot`
- CloudWatch Logs permissions

## Benefits
- Reduces unnecessary EBS snapshot storage costs.
- Automates stale resource cleanup.
- Improves AWS resource management.

## Important Note
Running and stopped instances are not the only consideration when deciding whether a snapshot is stale. Snapshots can be valuable backups even when their original volumes are no longer attached to an instance. Verify snapshot dependencies and backup requirements before deletion.

## Author
Darshan H S
