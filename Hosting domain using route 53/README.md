# Hosting a Domain with Route 53 and Configuring Path & Host-Based Routing via ALB

## 🛠️ Steps to Set Up

---

### 1. Domain Setup with Route 53

#### a. Buy a Domain
- Purchase a domain from any registrar like GoDaddy, Namecheap, or Hostinger.

<img width="1120" alt="Screenshot 2025-05-29 131256" src="https://github.com/user-attachments/assets/9093128c-01de-4b33-9836-5d403f626354" />


#### b. Create a Hosted Zone
- Go to the Route 53 console and create a hosted zone for your domain (e.g., `yourdomain.com`).

#### c. Update Name Servers
- Copy the NS records from Route 53.
- Go to your domain registrar’s DNS settings.
- Replace their NS records with the ones from Route 53.

#### d. Request an SSL Certificate (for HTTPS)
- Go to AWS Certificate Manager (ACM).
- Request a public certificate for `yourdomain.com` and `*.yourdomain.com`.
- Validate domain ownership by adding the provided CNAME record to your Route 53 hosted zone.

---

### 2. Application Setup on EC2

#### a. Launch EC2 Instances
- Install Nginx or any web server.
- Configure each application to listen on different ports (e.g., 80, 7764, 9097).

#### b. Create Target Groups
- Go to EC2 > Target Groups.
- Create a separate target group for each application.
- Register the corresponding EC2 instances and define health checks.

---

### 3. ALB Setup with Routing Rules

#### a. Create an Application Load Balancer
- Choose **Application Load Balancer**, internet-facing.
- Select 2 or more Availability Zones.
- Use the same VPC as your EC2 instances.
- Attach a security group that allows:
  - HTTP (port 80)
  - HTTPS (port 443)

#### b. Configure Listeners
- **HTTP Listener (Port 80)**
  - Add a redirect rule to forward all HTTP traffic to HTTPS.

- **HTTPS Listener (Port 443)**
  - Attach the SSL certificate from ACM.
  - Add routing rules:
    - Path-based routing: `/app1` → Target Group A
    - Host-based routing: `api.yourdomain.com` → Target Group B

---

### 4. DNS Configuration in Route 53

- Go to your domain’s hosted zone in Route 53.

#### Create an A Record
- **Record name**: `@` (root domain) or subdomain like `api`
- **Type**: A – IPv4 address
- **Alias**: Yes
- **Alias Target**: Select the ALB DNS name from the dropdown

✅ This connects your domain to the ALB, enabling secure HTTPS access and applying your routing rules.

<img width="1111" alt="Screenshot 2025-05-29 124832" src="https://github.com/user-attachments/assets/6ce1d231-3ac5-4439-b97d-161939e4867a" />

### Final Result

<img width="730" alt="Screenshot 2025-05-29 124942" src="https://github.com/user-attachments/assets/6c1bc521-0c3d-455f-a05a-bcd2c1fa8330" />

- All traffic is secured via HTTPS using ACM
    
  - Domain is managed via Route 53

<img width="770" alt="Screenshot 2025-05-29 125011" src="https://github.com/user-attachments/assets/876dcace-1a31-4433-885e-e74c332ea5d7" />


