# Deploying a Highly Available Web Application on AWS

## 📌 Overview
This project demonstrates the deployment of a **highly available**, **fault-tolerant**, and **scalable** web application on **AWS**. The architecture leverages AWS services such as **EC2 instances**, **Load Balancers**, **NAT Gateways**, and a **custom Virtual Private Cloud (VPC)** to ensure optimal performance and security.

![Overall Architecture](./img/overall-architecture.png)

---

## 🏗 Architecture Components
### 1️⃣ **Virtual Private Cloud (VPC) & Subnets**
A **custom VPC** is designed to host both **public** and **private** subnets across **two Availability Zones**, ensuring redundancy and fault tolerance.

📌 **Subnets Overview:**
- **Public Subnets:** Hosts internet-facing resources like the **Load Balancer** and **NAT Gateways**.
- **Private Subnets:** Houses **backend EC2 instances**, ensuring security and isolation.

📸 **VPC and Subnet Diagrams:**

![VPC](./img/vpc.png)
![Subnets](./img/subnets.png)

---

### 2️⃣ **Route Tables**
Proper routing configurations manage traffic flow between the subnets.

✅ **Public Subnets Route Table:**
- Routes internet traffic via the **Internet Gateway**.

![Route Table for Public Subnets](./img/public-route-table.png)

✅ **Private Subnets Route Tables:**
- Routes traffic through the **NAT Gateway** for secure outbound access.

![Route Table for Private Subnet 1](./img/private-route-table-1.png)
![Route Table for Private Subnet 2](./img/private-route-table-2.png)

---

### 3️⃣ **Gateways**
Two gateway types are implemented to manage inbound and outbound network traffic.

🚀 **Internet Gateway (IGW):**
- Provides internet access for **public subnets**.

![Internet Gateway](./img/internet-gateway.png)

🔒 **NAT Gateways:**
- Securely allows **private subnets** to access the internet without exposing them.

![NAT Gateway A](./img/nat-gateway-a.png)
![NAT Gateway B](./img/nat-gateway-b.png)

---

### 4️⃣ **EC2 Instances & Auto Scaling**
Two **EC2 instances** (Web_Server1 and Web_Server2) host the web application within the **private subnets**, ensuring security and performance.

📌 **Key Features:**
- **Auto Scaling Groups (ASG):** Automatically adjust the number of EC2 instances based on demand.
- **IAM Roles:** Grant secure access permissions to AWS resources.

📸 **EC2 Instances:**
![EC2 Instances](./img/ec2-instances.png)

📸 **IAM Role:**
![IAM Role](./img/iam-role.png)

---

### 5️⃣ **Load Balancer**
A **highly available Application Load Balancer (ALB)** distributes traffic across the EC2 instances to ensure fault tolerance.

📸 **Load Balancer Diagram:**
![Load Balancer](./img/load-balancer.png)

✅ **Target Groups:** Efficient traffic routing to backend instances.

![Target Group](./img/target-group.png)

---

### 6️⃣ **Security Groups & Access Control**
To protect the infrastructure, **strict access control policies** are enforced using AWS **Security Groups**.

🔒 **Key Configurations:**
- **Security Group for Web Traffic:** Allows HTTP(S) access to EC2 instances.
- **Security Group for Auto Scaling:** Controls inbound/outbound access for dynamic scaling.

📸 **Security Group for Web Traffic:**
![Security Group to enable Web Traffic to EC2 Instances](./img/security-group-1.png)

📸 **Security Group for Auto Scaling:**
![Security Group for the Auto Scaler](./img/security-group-2.png)