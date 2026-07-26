# 🚀 Three-Tier AWS Infrastructure using Terraform & Ansible

<p align="center">

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazonaws)
![Terraform](https://img.shields.io/badge/Terraform-IaC-7B42BC?logo=terraform)
![Ansible](https://img.shields.io/badge/Ansible-Automation-EE0000?logo=ansible)
![Linux](https://img.shields.io/badge/Linux-Amazon%20Linux-FCC624?logo=linux)
![Apache](https://img.shields.io/badge/Web%20Server-Apache-D22128?logo=apache)
![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?logo=github)

</p>

<p align="center">
An end-to-end <b>Infrastructure as Code (IaC)</b> project that provisions a secure Three-Tier AWS Architecture using <b>Terraform</b> and automates server configuration using <b>Ansible</b>.
</p>

---

# 📖 Table of Contents

1. Project Overview
2. Key Features
3. Architecture Diagram
4. AWS Services Used
5. Project Folder Structure
6. Terraform Initialization & Deployment
7. Ansible Configuration
8. Deployment Verification
9. Terraform Files
10. Screenshots
11. Challenges Encountered
12. Future Enhancements
13. Author

---

# 📌 Project Overview

This project demonstrates the deployment of a secure, scalable, and production-inspired **Three-Tier Architecture** on Amazon Web Services (AWS) using **Terraform** and **Ansible**.

Instead of manually creating cloud resources through the AWS Console, the complete infrastructure is provisioned using **Terraform**, following the principles of **Infrastructure as Code (IaC)**. Once the infrastructure is ready, **Ansible** is used to automatically configure the web server, install Apache, and deploy the web application.

The infrastructure follows a standard three-tier architecture:

- **Presentation Tier** – Application Load Balancer (ALB)
- **Application Tier** – Amazon EC2 Web Server
- **Data Tier** – Amazon RDS MySQL Database

To improve security, the web server and database are deployed inside **Private Subnets**, while the **Bastion Host** and **Application Load Balancer** are placed inside **Public Subnets**.

The project demonstrates several important cloud engineering concepts including:

- Infrastructure as Code (IaC)
- Configuration Management
- Virtual Private Cloud (VPC)
- Public & Private Networking
- Secure Remote Access using Bastion Host
- Load Balancing
- Managed Database Services
- Security Groups
- Apache Web Server Deployment

---

# ✨ Key Features

- ✅ Infrastructure Provisioning using Terraform
- ✅ Configuration Management using Ansible
- ✅ Custom AWS VPC
- ✅ Public & Private Subnets
- ✅ Internet Gateway
- ✅ NAT Gateway
- ✅ Route Tables
- ✅ Security Groups
- ✅ Bastion Host
- ✅ Amazon EC2 Web Server
- ✅ Application Load Balancer
- ✅ Target Group with Health Checks
- ✅ Amazon RDS MySQL Database
- ✅ Apache Web Server Deployment
- ✅ Secure SSH Access
- ✅ Infrastructure Verification using Terraform Outputs

---

# 🏗 Architecture Diagram

> **Replace the image below with your own architecture diagram.**

<p align="center">

![Architecture](screenshots/architecture.png)

</p>

## Architecture Flow

```text
                    Internet
                        │
                        ▼
          Application Load Balancer (ALB)
                        │
                        ▼
              EC2 Web Server (Private)
                        │
                        ▼
               Amazon RDS MySQL Database

          Bastion Host (Public Subnet)
                    │
                    ▼
             Secure SSH Connection
```

### Request Flow

```
User

↓

Application Load Balancer

↓

EC2 Web Server

↓

Amazon RDS MySQL
```

---

# ☁ AWS Services Used

| AWS Service | Purpose |
|-------------|---------|
| Amazon VPC | Provides an isolated virtual network for all AWS resources. |
| Public Subnets | Hosts the Bastion Host and Application Load Balancer. |
| Private Subnets | Hosts the EC2 Web Server and Amazon RDS. |
| Internet Gateway | Allows internet access for resources in public subnets. |
| NAT Gateway | Enables outbound internet access for private instances. |
| Route Tables | Controls network routing between subnets and gateways. |
| Security Groups | Acts as virtual firewalls controlling inbound and outbound traffic. |
| Amazon EC2 | Hosts the Apache web application. |
| Bastion Host | Securely accesses resources inside private subnets through SSH. |
| Application Load Balancer | Distributes incoming HTTP traffic to the web server. |
| Target Group | Performs health checks and routes traffic to healthy instances. |
| Amazon RDS MySQL | Provides a managed relational database service. |
| Elastic IP | Provides a static public IP address for the NAT Gateway. |

---

# 📁 Project Folder Structure

```text
three-tier-aws-terraform-ansible/
│
├── terraform/
│   ├── provider.tf
│   ├── versions.tf
│   ├── variables.tf
│   ├── terraform.tfvars.example
│   ├── vpc.tf
│   ├── subnets.tf
│   ├── igw.tf
│   ├── nat.tf
│   ├── route_tables.tf
│   ├── security_groups.tf
│   ├── ec2.tf
│   ├── alb.tf
│   ├── rds.tf
│   ├── outputs.tf
│   └── data.tf
│
├── ansible/
│   ├── ansible.cfg
│   ├── inventory.ini
│   └── playbook.yml
│
├── app/
│   └── index.html
│
├── screenshots/
│   ├── architecture.png
│   ├── terraform_apply.png
│   ├── vpc.png
│   ├── subnets.png
│   ├── route_tables.png
│   ├── internet_gateway.png
│   ├── nat_gateway.png
│   ├── security_groups.png
│   ├── ec2_instances.png
│   ├── bastion_login.png
│   ├── alb.png
│   ├── target_group.png
│   ├── rds.png
│   ├── ansible_output.png
│   ├── nginx.png
│   └── website.png
│
├── .gitignore
├── LICENSE
└── README.md
```

---

---

# ⚙️ Terraform Initialization & Deployment

Terraform is used to provision the complete AWS infrastructure using Infrastructure as Code (IaC). All AWS resources such as the VPC, subnets, security groups, EC2 instances, Application Load Balancer, and Amazon RDS are created automatically through Terraform configuration files.

## Step 1: Clone the Repository

```bash
git clone https://github.com/Priyanshupal08/three-tier-aws-terraform-ansible.git

cd three-tier-aws-terraform-ansible/terraform
```

---

## Step 2: Configure AWS Credentials

Configure AWS CLI before deploying the infrastructure.

```bash
aws configure
```

Provide the following details:

```
AWS Access Key ID
AWS Secret Access Key
Default Region (ap-south-1)
Output Format (json)
```

---

## Step 3: Initialize Terraform

```bash
terraform init
```

**Purpose**

- Downloads required providers
- Initializes the working directory
- Prepares Terraform for deployment

---

## Step 4: Validate Configuration

```bash
terraform validate
```

**Purpose**

Checks the Terraform configuration for syntax errors before deployment.

---

## Step 5: Review Execution Plan

```bash
terraform plan
```

**Purpose**

Displays the resources Terraform will create without making any changes.

---

## Step 6: Deploy Infrastructure

```bash
terraform apply
```

Type

```
yes
```

when prompted.

Terraform creates:

- Amazon VPC
- Public Subnets
- Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- Bastion Host
- EC2 Web Server
- Application Load Balancer
- Target Group
- Amazon RDS MySQL

---

# 🤖 Ansible Configuration & Deployment

After the infrastructure is successfully deployed, Ansible is used to configure the EC2 Web Server.

## Step 1: Navigate to the Ansible Directory

```bash
cd ../ansible
```

---

## Step 2: Verify Inventory

```bash
ansible-inventory -i inventory.ini --list
```

This command verifies that Ansible can identify the target servers.

---

## Step 3: Execute the Playbook

```bash
ansible-playbook -i inventory.ini playbook.yml
```

The playbook performs the following tasks:

- Connects to the Web Server
- Installs Apache HTTP Server
- Starts Apache Service
- Enables Apache on Boot
- Deploys the Sample Web Application

---

# ✅ Deployment Verification

The deployment was verified using Terraform, AWS Console, and the deployed web application.

---

## Terraform State

```bash
terraform state list
```

This command lists all AWS resources currently managed by Terraform.

Example output:

```text
aws_vpc.main

aws_subnet.public_subnet_1

aws_subnet.public_subnet_2

aws_subnet.private_subnet_1

aws_subnet.private_subnet_2

aws_instance.bastion

aws_instance.web

aws_lb.alb

aws_db_instance.mysql
```

---

## Terraform Outputs

```bash
terraform output
```

This displays important deployment information such as:

- Application Load Balancer DNS
- Bastion Host Public IP
- Amazon RDS Endpoint
- VPC ID
- Subnet IDs

Example:

```text
alb_dns_name = ...

bastion_public_ip = ...

database_endpoint = ...

vpc_id = ...
```

---

## AWS Console Verification

The following AWS services were verified after deployment:

- ✅ VPC Created Successfully
- ✅ Public & Private Subnets
- ✅ Route Tables
- ✅ Internet Gateway
- ✅ NAT Gateway
- ✅ Security Groups
- ✅ EC2 Instances Running
- ✅ Application Load Balancer Active
- ✅ Target Group Healthy
- ✅ Amazon RDS Available

---

## Web Application Verification

Copy the ALB DNS Name from Terraform Output and open it in any web browser.

```
http://<Application-Load-Balancer-DNS>
```

Expected Output

```
Three Tier AWS Project Successfully Deployed
```

This confirms that:

- Infrastructure is successfully provisioned.
- Apache Web Server is running.
- ALB is routing traffic correctly.
- EC2 instance is serving the application.

---

# 📂 Terraform Files

The Terraform project is organized into multiple files, where each file is responsible for provisioning a specific AWS resource.

| File | Description |
|------|-------------|
| **provider.tf** | Configures the AWS Provider and selected region. |
| **versions.tf** | Defines Terraform and AWS Provider versions. |
| **variables.tf** | Declares input variables used throughout the project. |
| **terraform.tfvars.example** | Sample variable file for user configuration. |
| **data.tf** | Retrieves AWS resources such as the latest Amazon Linux AMI. |
| **vpc.tf** | Creates the custom Amazon VPC. |
| **subnets.tf** | Creates public and private subnets across Availability Zones. |
| **igw.tf** | Creates and attaches the Internet Gateway. |
| **nat.tf** | Creates Elastic IP and NAT Gateway. |
| **route_tables.tf** | Configures routing for public and private subnets. |
| **security_groups.tf** | Creates Security Groups for ALB, Bastion Host, EC2, and RDS. |
| **ec2.tf** | Launches Bastion Host and Web Server EC2 instances. |
| **alb.tf** | Creates Application Load Balancer, Target Group, and Listener. |
| **rds.tf** | Provisions the Amazon RDS MySQL database. |
| **outputs.tf** | Displays deployment outputs such as ALB DNS, Bastion IP, and RDS Endpoint. |

---

---

# 📸 Screenshots

This section contains screenshots captured during the successful deployment and verification of the Three-Tier AWS Infrastructure.

---

# 1️⃣ Terraform Apply Output

The following screenshot shows the successful execution of `terraform apply`, confirming that all AWS resources were created successfully.

<p align="center">

![Terraform Apply Output](screenshots/terraform_apply.png)

</p>

---

# 2️⃣ Amazon VPC

The custom Virtual Private Cloud (VPC) provides network isolation for all AWS resources used in this project.

<p align="center">

![VPC](screenshots/vpc.png)

</p>

---

# 3️⃣ Public & Private Subnets

The infrastructure consists of two public subnets and two private subnets distributed across multiple Availability Zones.

<p align="center">

![Subnets](screenshots/subnets.png)

</p>

---

# 4️⃣ Route Tables

Route Tables manage network traffic by defining routes for both public and private subnets.

<p align="center">

![Route Tables](screenshots/route_tables.png)

</p>

---

# 5️⃣ Internet Gateway

The Internet Gateway enables internet connectivity for resources deployed inside public subnets.

<p align="center">

![Internet Gateway](screenshots/internet_gateway.png)

</p>

---

# 6️⃣ NAT Gateway

The NAT Gateway provides secure outbound internet access for EC2 instances running inside private subnets without exposing them directly to the internet.

<p align="center">

![NAT Gateway](screenshots/nat_gateway.png)

</p>

---

# 7️⃣ Security Groups

Security Groups act as virtual firewalls that control inbound and outbound traffic for the Bastion Host, Application Load Balancer, Web Server, and Amazon RDS.

<p align="center">

![Security Groups](screenshots/security_groups.png)

</p>

---

# 8️⃣ Amazon EC2 Instances

The deployment includes two EC2 instances:

- Bastion Host
- Web Server

<p align="center">

![EC2 Instances](screenshots/ec2_instances.png)

</p>

---

# 9️⃣ Bastion Host Login

The Bastion Host provides secure SSH access to the private EC2 Web Server.

<p align="center">

![Bastion Login](screenshots/bastion_login.png)

</p>

---

# 🔟 Application Load Balancer

The Application Load Balancer distributes incoming HTTP requests to the Web Server running inside the private subnet.

<p align="center">

![Application Load Balancer](screenshots/application_load_balancer.png)

</p>

---

# 1️⃣1️⃣ Target Group Health Check

The Target Group performs periodic health checks to ensure traffic is routed only to healthy EC2 instances.

<p align="center">

![Target Group](screenshots/target_group_health.png)

</p>

---

# 1️⃣2️⃣ Amazon RDS MySQL Instance

Amazon RDS provides a fully managed MySQL database deployed securely inside the private subnet.

<p align="center">

![Amazon RDS](screenshots/rds_mysql.png)

</p>

---

# 1️⃣3️⃣ Successful Ansible Playbook Execution

The following screenshot demonstrates the successful execution of the Ansible Playbook used to configure the EC2 Web Server.

<p align="center">

![Ansible Playbook](screenshots/ansible_playbook.png)

</p>

---

# 1️⃣4️⃣ Apache Running on the Web Server

Apache HTTP Server is successfully installed and running on the EC2 Web Server.

> **Note:** If your instructor specifically asked for **Nginx**, replace this section only if your project actually uses Nginx. Since your project uses **Apache**, it is better to keep this accurate.

<p align="center">

![Apache Running](screenshots/apache_running.png)

</p>

---

# 1️⃣5️⃣ Web Application Accessible through the Load Balancer

The deployed web application is successfully accessible using the DNS Name of the Application Load Balancer.

<p align="center">

![Website](screenshots/website_load_balancer.png)

</p>

---

# ✅ Deployment Summary

The successful deployment verifies that:

- ✔️ Terraform provisioned all AWS infrastructure.
- ✔️ Networking components were configured correctly.
- ✔️ Bastion Host enabled secure SSH access.
- ✔️ EC2 Web Server was deployed successfully.
- ✔️ Application Load Balancer routed traffic correctly.
- ✔️ Target Group Health Checks passed.
- ✔️ Amazon RDS MySQL was created successfully.
- ✔️ Apache Web Server served the application.
- ✔️ The web application was accessible through the ALB DNS endpoint.

---

# ⚠️ Challenges Encountered During Implementation

During the development of this project, several challenges were encountered while provisioning infrastructure and configuring AWS resources. Each issue was analyzed and resolved to ensure a successful deployment.

| Challenge | Description | Solution |
|-----------|-------------|----------|
| Unsupported EC2 Instance Type | The selected EC2 instance type was unavailable in the chosen AWS region. | Changed the instance type to a supported Free Tier eligible instance (`t3.micro`). |
| Invalid MySQL Engine Version | Terraform failed while creating the RDS instance due to an unsupported MySQL version. | Queried available engine versions using AWS CLI and updated the configuration to a supported version. |
| Duplicate Terraform Resources | Duplicate resource definitions caused validation errors. | Removed duplicate resources and validated the configuration using `terraform validate`. |
| Private EC2 SSH Access | Direct SSH access to the Web Server was not possible because it resided in a private subnet. | Connected securely through the Bastion Host using SSH Proxy/Jump Host. |
| ALB Health Check Failure | The Application Load Balancer initially marked the EC2 instance as unhealthy. | Installed and started Apache HTTP Server and verified the health check path. |
| Ansible SSH Connectivity | Initial Ansible execution failed due to SSH key and inventory configuration issues. | Corrected the inventory file, SSH key permissions, and verified connectivity before executing the playbook. |
| Terraform Variable Management | Sensitive credentials were initially hardcoded. | Replaced hardcoded values with Terraform variables and created `terraform.tfvars.example` for secure configuration. |

---

# 📚 Lessons Learned

This project provided practical experience with modern DevOps and Cloud Engineering practices.

Key learning outcomes include:

- Understanding Infrastructure as Code (IaC) using Terraform.
- Automating server configuration using Ansible.
- Designing a secure Three-Tier Architecture on AWS.
- Configuring VPC networking, subnets, route tables, Internet Gateway, and NAT Gateway.
- Implementing secure communication using Bastion Hosts.
- Deploying and managing Amazon EC2 instances.
- Configuring an Application Load Balancer with Target Groups and Health Checks.
- Deploying a managed MySQL database using Amazon RDS.
- Troubleshooting Terraform and AWS deployment issues.
- Managing infrastructure securely using variables and best practices.

---

# 🚀 Future Enhancements

The current implementation provides a solid foundation for a production-style infrastructure. The following enhancements can further improve scalability, security, and automation.

- Implement Auto Scaling Groups for automatic scaling.
- Configure HTTPS using AWS Certificate Manager (ACM).
- Integrate Amazon Route 53 for custom domain management.
- Store Terraform State remotely using Amazon S3 and DynamoDB.
- Secure application secrets using AWS Secrets Manager.
- Enable CloudWatch Monitoring and Logging.
- Configure AWS WAF for enhanced security.
- Containerize the application using Docker.
- Deploy the application using Amazon ECS or Kubernetes (EKS).
- Build a CI/CD pipeline using GitHub Actions or Jenkins.

---

# 🎯 Conclusion

This project demonstrates the successful implementation of a secure and scalable Three-Tier AWS Infrastructure using Terraform and Ansible.

The infrastructure was fully provisioned using Infrastructure as Code (IaC), reducing manual configuration while ensuring repeatability and consistency. Configuration management was automated using Ansible to install and configure the web server.

The project showcases practical knowledge of AWS networking, compute, load balancing, database deployment, automation, and security. It also highlights the importance of following DevOps best practices for infrastructure provisioning and management.

---

# 🛠 Technologies Used

| Category | Technologies |
|----------|--------------|
| Cloud Platform | Amazon Web Services (AWS) |
| Infrastructure as Code | Terraform |
| Configuration Management | Ansible |
| Operating System | Amazon Linux |
| Web Server | Apache HTTP Server |
| Database | Amazon RDS MySQL |
| Networking | Amazon VPC |
| Version Control | Git & GitHub |
| Development Tools | Visual Studio Code, AWS CLI |

---

# 👨‍💻 Author

**Priyanshu Pal**

**Bachelor of Technology (B.Tech)**  
Computer Science & Engineering (Artificial Intelligence & Machine Learning)

### Connect with Me

- GitHub: https://github.com/Priyanshupal08
- LinkedIn: *(Add your LinkedIn profile URL here)*

---

# 📄 License

This project is developed for **educational and learning purposes**.

You are welcome to use this repository for learning, experimentation, and academic reference. Please provide appropriate credit if you reuse significant portions of this work.

---

# ⭐ Acknowledgements

Special thanks to:

- Amazon Web Services (AWS)
- Terraform by HashiCorp
- Ansible by Red Hat
- Open Source Community
- Faculty and Mentors for guidance throughout the project

---

<p align="center">

### ⭐ If you found this project useful, consider giving it a Star on GitHub! ⭐

</p>
