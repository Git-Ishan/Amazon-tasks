# Path-Based Routing with Application Load Balancer (ALB) 

## Set up an Application Load Balancer (ALB) that routes HTTP requests based on the request path:

http://<ALB-DNS>/app1 → forwarded to Target Group A

http://<ALB-DNS>/app2 → forwarded to Target Group B

### 1️. Launch Two EC2 Instances

One instance serves the /app1 path 

Another serves the /app2 path

<img width="760" alt="1" src="https://github.com/user-attachments/assets/e88e86a2-50fb-45ce-b9d9-f11d4eb0b56a" />

Install a web server (e.g., Nginx) on both and configure different content for each path.

<img width="758" alt="2" src="https://github.com/user-attachments/assets/6a351452-f86a-4d9a-bac5-82bd9e5b58c7" />

<img width="761" alt="3" src="https://github.com/user-attachments/assets/bc40ebf6-5505-4f47-b9d5-fd39ca857815" />

### 2. Create Two Target Groups

Target Group A: Register the EC2 instance serving /app1

Target Group B: Register the EC2 instance serving /app2

<img width="767" alt="4" src="https://github.com/user-attachments/assets/7e778c78-819c-44fb-9d84-eb76d6508f6a" />

### 3. Create an Application Load Balancer

Choose Application Load Balancer, set it to internet-facing

Select at least two subnets across different availability zones

Attach a Security Group that allows inbound HTTP (port 80)

<img width="763" alt="5" src="https://github.com/user-attachments/assets/e08b1cee-57ff-4170-8436-b7d07370918e" />

### 4. Configure Listener & Routing Rules

Listener: HTTP on port 80

Rules:

- If path is /app2, forward to Target Group B

- Default rule (i.e., /app1) forwards to Target Group A

<img width="742" alt="6" src="https://github.com/user-attachments/assets/4b7d8454-15cb-40e8-a5fa-ebe670246d49" />

### 5.  Test the Routing

Open a browser and verify:


<img width="748" alt="7" src="https://github.com/user-attachments/assets/5b7324ef-c8ad-4eb6-a3d6-77fc1e042b01" />

<img width="766" alt="8" src="https://github.com/user-attachments/assets/49e2f3b8-daf7-41ea-b3b2-8075db56e4f9" />
