# Connect to a Private EC2 Instance Using a Bastion Host #

Steps :

### 1. Create a VPC
  `CIDR block: 10.0.0.0/16`
  
<img width="1088" alt="1" src="https://github.com/user-attachments/assets/13e92ff1-dbc2-4a5d-b336-fe32c2e68572" />


### 2. Create Two Subnets: 

  `Public Subnet: 10.0.1.0/24`

  `Private Subnet: 10.0.2.0/24`

<img width="760" alt="2" src="https://github.com/user-attachments/assets/367a50ab-297e-4397-8c4d-3fa4cc9b998d" />

### 3. Set Up Internet Access

a. Create an Internet Gateway and attach it to your VPC

<img width="1109" alt="3" src="https://github.com/user-attachments/assets/f71df00b-e058-4fd8-a5f8-b97ebf2a8457" />

b. Update the route table for the public subnet:

Add route 0.0.0.0/0 → target the Internet Gateway

<img width="761" alt="4" src="https://github.com/user-attachments/assets/4b8e66d8-21c2-4869-b35e-fbe07432e8d7" />

### 4. Launch EC2 Instances

One in the public subnet = Bastion host

One in the private subnet = Private instance

Use different key pairs for both:

Bastion EC2 → bastion.pem

Private EC2 → pvt-key.pem


### 5. SSH into the Bastion Host

From your local system, run:

  `ssh -i "path/to/bastion-key.pem" ubuntu@<public-ip-of-bastion>`
  
Send the Private Key to Bastion Host

![5](https://github.com/user-attachments/assets/e1417dc9-b5bd-401f-82ea-240191091db7)


Still from your local machine, send the private EC2 key:

  `scp -i "path/to/bastion-key.pem" path/to/private-key.pem ubuntu@<public-ip-of-bastion>:~`
  
SSH into Bastion Again & Set Permissions

chmod 400 private-key.pem

Now SSH into the Private EC2 from Bastion Host

  `ssh -i private-key.pem ubuntu@<private-ip-of-private-ec2>`

<img width="601" alt="Screenshot 2025-05-29 125709" src="https://github.com/user-attachments/assets/b6d4a010-4473-4f4e-b76c-2487d4141e45" />
