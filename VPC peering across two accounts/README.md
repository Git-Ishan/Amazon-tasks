# VPC Peering Across Two AWS Accounts

## Establish connectivity between two EC2 instances hosted in separate VPCs across two different AWS accounts using VPC Peering, and verify it using a ping (ICMP) test.

Steps :

### 1. Create Two VPCs

a. Create one VPC in each AWS account (e.g., 10.0.0.0/16 and 20.0.0.0/16).

b. Ensure the CIDR blocks do not overlap.


### 2. Attach Internet Gateway

a. For each VPC, create and attach an Internet Gateway (IGW).

b. Update the Route Table to allow internet access for external communication (optional for peering, useful for package installations or SSH).

### 3.  Create Subnets

a. Create one or more subnets in each VPC (e.g., 10.0.1.0/24 in VPC-A and 20.0.1.0/24 in VPC-B).

b. Associate subnets with appropriate route tables.

### 4. Create a VPC Peering Connection

a. In one AWS account (Requester), go to VPC > Peering Connections and:
  - Click Create Peering Connection
  - Select My Account or Another Account
  = Provide the Account ID and VPC ID of the other account (Accepter)

### 5. Accept the Peering Request

a. In the second account, go to Peering Connections

b. Select the request and click Accept

### 6.  Update Route Tables

a. In both VPCs, edit the Route Tables:
  - Add a route for the other VPC’s CIDR block
  - Target: The VPC Peering Connection ID

### 7. Launch EC2 Instances

a. Launch one EC2 instance in each VPC

b. Place each instance in the respective subnet

c. Ensure both instances are in public subnets or reachable within their respective VPCs

### 8. Configure Security Groups (NSG)

a. Allow ICMP (Echo Request) in the Security Groups of both EC2s
  - Type: All ICMP - IPv4
  - Source: The CIDR block of the other VPC (not just the instance IP)

### 9. Ping Test

a. SSH into one EC2 instance
  -  Run `ping <Private-IP-of-other-EC2>`
  - You should see ICMP responses if everything is set up correctly.

![vpc peering](https://github.com/user-attachments/assets/09c54fe9-8f0d-4d12-9418-0b7ebbf9847b)

### Successfully established cross-account VPC Peering, configured routing and security, and verified network-level connectivity using ping.
