# Deploying a Highly Available Web Application on AWS

## Overview
This project demonstrates the deployment of a highly available and fault-tolerant web application on AWS. The architecture ensures resilience, scalability, and security by leveraging AWS resources such as EC2 instances, a load balancer, NAT Gateways, and a custom Virtual Private Cloud (VPC).
![Overall Architecture](./img/overall-architecture.png)

## Architecture Components
### 1. **Virtual Private Cloud (VPC) and Subnets**
- A custom VPC hosting both public and private subnets across two availability zones.
![VPC](./img/vpc.png)
- **Public Subnets:** Hosts resources requiring internet access, such as the load balancer and NAT Gateways.
- **Private Subnets:** Hosts backend EC2 instances, ensuring security and isolation.
![Subnets](./img/subnets.png)

### 2. **Route Tables**
- Configured for both public and private subnets to manage traffic flow effectively.
#### **Public Subnets Route Table**
![Route Table for Public Subnets](./img/public-route-table.png)

#### **Private Subnets Route Tables**
![Route Table for Private Subnet 1](./img/private-route-table-1.png)
![Route Table for Private Subnet 2](./img/private-route-table-2.png)

### 3. **Gateways**
- **Internet Gateway:** Allows communication between public subnets and the internet.
![Internet Gateway](./img/internet-gateway.png)

- **NAT Gateways:** Provides secure internet access for private subnets.
![NAT Gateway A](./img/nat-gateway-a.png)
![NAT Gateway B](./img/nat-gateway-b.png)

### 4. **EC2 Instances**
- Web application backend hosted on two EC2 instances (Web_Server1 and Web_Server2) in private subnets.
![EC2 Instances](./img/ec2-instances.png)
- Auto Scaling Groups (ASG) ensure elasticity by dynamically adjusting instances based on demand.
- IAM Roles assigned for secure access management.
![IAM Role](./img/iam-role.png)

### 5. **Load Balancer**
- A highly available load balancer distributes incoming traffic across EC2 instances.
![Load Balancer](./img/load-balancer.png)
- Target groups are used for efficient traffic routing.
![Target Group](./img/target-group.png)

### 6. **Security Groups**
- Configured to enforce strict access controls and protect resources from unauthorized access.
![Security Group to enable Web Traffic to EC2 Instances](./img/security-group-1.png)
![Security Group for the Auto Scaler](./img/security-group-2.png)