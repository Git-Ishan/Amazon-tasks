# Auto Scaling EC2 Instances Using Launch Templates and AMI 


## Step-by-Step Setup

### 1. Create a EC2 Instance

- Choose a base AMI (Amazon Linux 2 or Ubuntu)
- Launch the instance

<img width="896" alt="1" src="https://github.com/user-attachments/assets/a3eba666-0d6f-441d-b037-fcc805f3d993" />


### 2. Create an AMI (Amazon Machine Image)

- Once the EC2 is configured:
  - Go to Actions → Image → Create Image
  - Name it (e.g., `ASG-custom-AMI`)

<img width="906" alt="2" src="https://github.com/user-attachments/assets/08291c3f-9063-4ded-9625-e9f5bc28b371" />


### 3. Create a Launch Template

  - Name: `ASG-Launch-Template`
  - AMI: Use the AMI created above
  - Instance Type: e.g., `t2.micro`
  - Security Group : Allow HTTP (port 80) and SSH (port 22)  
  - Launch Template

<img width="902" alt="3" src="https://github.com/user-attachments/assets/664b58d9-871d-46d1-b859-d7442c64e2fd" />


### 4. Create Auto Scaling Group (ASG)

- Name your ASG (e.g., `ASG-test-group`)
- Choose Launch Template you created
- Select VPC and Subnets
- Set Desired, Min, and Max capacity:
  - Desired: `1`, Min: `1`, Max: `3`

<img width="1069" alt="4" src="https://github.com/user-attachments/assets/daf4c08b-4500-4157-adcc-25c912da31bc" />

- Click Create Auto Scaling Group

<img width="913" alt="5" src="https://github.com/user-attachments/assets/f9bbb1d7-1c64-4fb1-a58d-a0b32176c972" />

# Testing Auto Scaling

1. EC2 → Instances
<img width="899" alt="6" src="https://github.com/user-attachments/assets/c33398b6-b763-4af2-97f9-a4bcd517a6fa" />

2. Terminate one instance launched by ASG
   
3. ASG will automatically launch a new instance to maintain capacity
<img width="911" alt="7" src="https://github.com/user-attachments/assets/6e411e07-fed7-4ba5-a1ea-7185d3b75bc2" />
