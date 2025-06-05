# EC2 Snapshot, AMI Creation, and Data Consistency – AWS Workflow

## 1. Launch Initial EC2 Instance

<img width="1100" alt="1" src="https://github.com/user-attachments/assets/1b62a514-a084-4599-b2e3-8c92b649f8f3" />

## 2. Add Files to EBS Root Volume


## 3. Create Snapshot of the Root Volume

<img width="1112" alt="2" src="https://github.com/user-attachments/assets/df95d2a1-7c23-454d-87a0-169f6a99df8a" />


## 4. Create EBS Volume from Snapshot

<img width="1096" alt="3" src="https://github.com/user-attachments/assets/0e8757a0-87b3-4ffe-bafd-dae93915326e" />


## 5. Create AMI from Snapshot

<img width="1103" alt="4" src="https://github.com/user-attachments/assets/aecd6fee-a00a-4fc4-864b-4094a404de9c" />


## 6. Launch EC2 from New AMI

## 7. Launch EC2 and Attach EBS Volume

- SSH into the EC2 and mount the volume
- You should see the files and directories from the original instance here as well.

## Summary

By using both EBS Snapshots and custom AMIs, we demonstrated how to:

Back up and clone EC2 environments

Recover data efficiently

Ensure system consistency

Support scaling and disaster recovery strategies in AWS
