# Creating a Custom IAM Policy

This IAM policy is designed to provide limited EC2 instance control with the following permissions and restrictions:

a. Start and Stop Instances (us-east-1 only):
The user is allowed to start and stop EC2 instances, but only within the us-east-1 (N. Virginia) region. This ensures control is limited to a specific AWS region.

b. View EC2 Instances Across All Regions:
The user has read-only access to describe and list EC2 instances (DescribeInstances) in any region, enabling visibility into existing infrastructure.

c. Deny Termination of Instances (All Regions):
The policy explicitly denies the ability to terminate EC2 instances (TerminateInstances), preventing accidental or unauthorized deletion of any instan

<img width="478" alt="policy" src="https://github.com/user-attachments/assets/e2debbc7-9e3d-4771-881b-aca10db11688" />

