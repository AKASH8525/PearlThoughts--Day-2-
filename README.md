# Cloud Computing and AWS Fundamentals

This repository contains structured notes covering **Cloud Computing basics**, **AWS core services**, and **networking fundamentals** required for cloud and DevOps roles.

---

## 1. Cloud Computing – Fundamentals

### 1.1 What is Cloud Computing?

Cloud computing is the delivery of computing resources such as servers, storage, databases, networking, and software over the internet instead of using local or on-premises hardware.

Users can access resources on demand and pay only for what they use.

---

### 1.2 Why Cloud Computing is Used

* Eliminates the need for physical infrastructure
* Provides scalability and flexibility
* Reduces operational and capital costs
* Enables faster application deployment
* Offers high availability and reliability

---

### 1.3 Core Components of Cloud Computing

* **Compute** – Virtual machines and processing power
* **Storage** – Object, block, and file storage
* **Networking** – Virtual networks, routing, and connectivity
* **Databases** – Managed relational and non-relational databases
* **Security** – Identity management, access control, and firewalls

---

### 1.4 Cloud Service Models

#### Infrastructure as a Service (IaaS)

* User manages operating system and applications
* Cloud provider manages hardware and virtualization

#### Platform as a Service (PaaS)

* User focuses on application development
* Cloud provider manages OS, runtime, and infrastructure

#### Software as a Service (SaaS)

* Fully managed software accessed via the internet
* No infrastructure or platform management required

---

### 1.5 Cloud Deployment Models

#### Public Cloud

* Infrastructure shared among multiple users
* Most commonly used deployment model

#### Private Cloud

* Dedicated infrastructure for a single organization
* Higher control and security

#### Hybrid Cloud

* Combination of public and private cloud
* Allows workload flexibility

---

### 1.6 Real World Use Case

A company hosts its website on the cloud instead of purchasing physical servers.
The website scales automatically during high traffic and reduces resources during low usage, while paying only for consumed resources.

---

## 2. Introduction to Amazon Web Services (AWS)

### 2.1 What is AWS?

Amazon Web Services (AWS) is a cloud computing platform that provides on-demand services such as compute, storage, networking, databases, security, and analytics.

---

### 2.2 Why AWS is Used

* Wide range of cloud services
* Global infrastructure with high availability
* Scalable and flexible resources
* Pay-as-you-go pricing model
* Strong security and compliance

---

### 2.3 AWS Global Infrastructure

* **Region** – Geographical area
* **Availability Zone (AZ)** – Isolated data centers within a region
* **Edge Location** – Used for content delivery and low latency

This design enables fault tolerance and high availability.

---

### 2.4 AWS Shared Responsibility Model

**AWS Responsibility**

* Physical data centers
* Hardware and networking
* Infrastructure security

**Customer Responsibility**

* Data security
* Application security
* IAM, OS patching, configuration

---

### 2.5 AWS Service Categories

* **Compute** – EC2, Auto Scaling
* **Storage** – S3
* **Networking** – VPC, Load Balancer
* **Database** – RDS
* **Security** – IAM
* **Monitoring** – CloudWatch

---

### 2.6 Real World Use Case

A company hosts applications on AWS using EC2, stores data in S3, manages access using IAM, and scales automatically without owning physical servers.

---

## 3. CIDR (Classless Inter-Domain Routing)

### 3.1 What is CIDR?

CIDR is a method used to define IP address ranges and is essential for cloud network design.

Format:

```
IP_address/Prefix_length
```

Example:

```
10.0.0.0/16
```

---

### 3.2 Why CIDR is Used

* Efficient IP address management
* Avoids IP wastage
* Required for VPC and subnet design
* Enables scalable networking

---

### 3.3 Key CIDR Concepts

* **IP Address** – Identifies a device
* **Prefix Length** – Number of network bits
* **Network Portion** – Fixed part
* **Host Portion** – Variable part

Example:

```
10.0.0.0/16
```

---

### 3.4 CIDR in AWS

* CIDR must be defined before creating a VPC
* VPC CIDR cannot be changed
* Subnet CIDRs must be within VPC range
* CIDR blocks must not overlap

**Private CIDR ranges**

* 10.0.0.0/8
* 172.16.0.0/12
* 192.168.0.0/16

---

### 3.5 CIDR Planning Example

* VPC: `10.0.0.0/16`
* Public Subnet: `10.0.1.0/24`
* Private Subnet: `10.0.2.0/24`

---

### 3.6 Real World Use Case

Organizations plan CIDR blocks to ensure unique IP allocation for EC2, databases, and services without conflicts.

---

## 4. VPC (Virtual Private Cloud)

### 4.1 What is a VPC?

A VPC is a logically isolated virtual network in AWS where users can deploy and manage cloud resources.

---

### 4.2 Why VPC is Used

* Network isolation
* Custom IP address range
* Secure internal communication
* Supports public and private networking

---

### 4.3 Core Components of a VPC

* CIDR Block
* Subnets
* Route Tables
* Internet Gateway
* NAT Gateway
* Security Groups

---

### 4.4 VPC CIDR Rules

* Defined during creation
* Cannot be modified later
* Subnets must fall within CIDR
* No overlapping networks

---

### 4.5 Basic VPC Creation Steps

1. Open AWS Console
2. Go to VPC
3. Create VPC
4. Enter name and CIDR
5. Select tenancy
6. Create

---

### 4.6 Real World Use Case

Public subnets host web servers while private subnets host databases for secure access.

---

## 5. Subnets (Public and Private)

### 5.1 What is a Subnet?

A subnet is a smaller network within a VPC created by dividing the CIDR block.

---

### 5.2 Why Subnets are Used

* Logical separation
* Controlled internet access
* Improved security
* Fault-tolerant architecture

---

### 5.3 Types of Subnets

**Public Subnet**

* Route to Internet Gateway
* Used for web servers and load balancers

**Private Subnet**

* No direct internet access
* Uses NAT Gateway
* Used for databases and backend services

---

### 5.4 Subnet CIDR Rules

* Must be within VPC CIDR
* Must not overlap
* Smaller CIDR means fewer IPs

---

### 5.5 Subnet Creation Steps

1. AWS Console
2. VPC → Subnets
3. Create Subnet
4. Select VPC and AZ
5. Enter CIDR
6. Create

---

### 5.6 Real World Use Case

Web servers are placed in public subnets, and databases in private subnets to improve security.

---

## 6. Internet Gateway (IGW) and NAT Gateway

### 6.1 Internet Gateway

Allows communication between VPC resources and the internet.

---

### 6.2 NAT Gateway

Allows outbound internet access for private subnet resources without inbound access.

---

### 6.3 IGW vs NAT Gateway

| Feature  | Internet Gateway   | NAT Gateway    |
| -------- | ------------------ | -------------- |
| Used In  | Public Subnet      | Private Subnet |
| Access   | Inbound & Outbound | Outbound only  |
| Use Case | Web servers        | Databases      |

---

### 6.4 Real World Use Case

Public web servers use IGW, while private backend servers use NAT Gateway for secure updates.

---

## 7. Route Tables

### 7.1 What is a Route Table?

Defines how traffic is routed within a VPC.

---

### 7.2 Types of Route Tables

* **Public Route Table** – Routes to IGW
* **Private Route Table** – Routes to NAT Gateway

---

### 7.3 Real World Use Case

Ensures public traffic reaches web servers and private resources remain protected.

---

## 8. Security Groups

### 8.1 What is a Security Group?

A virtual firewall controlling inbound and outbound traffic at the instance level.

---

### 8.2 Key Characteristics

* Stateful
* Allow rules only
* Instance-level protection
* Reusable

---

### 8.3 Common Rules

* SSH – Port 22
* HTTP – Port 80
* HTTPS – Port 443

---

### 8.4 Security Group vs Network ACL

| Feature | Security Group | Network ACL    |
| ------- | -------------- | -------------- |
| Level   | Instance       | Subnet         |
| Type    | Stateful       | Stateless      |
| Rules   | Allow only     | Allow and deny |

---

## 9. Virtual Machines and EC2

### 9.1 Virtual Machine

A software-based computer running inside a physical server.

---

### 9.2 Amazon EC2

Provides resizable compute capacity in the cloud.

---

### 9.3 EC2 Components

* AMI
* Instance Type
* Key Pair
* Security Group
* EBS Volume

---

### 9.4 EC2 Use Case

Applications scale by launching or terminating EC2 instances based on traffic.

---

## 10. RDS (Relational Database Service)

### 10.1 What is RDS?

A managed relational database service that automates backups, patching, and scaling.

---

### 10.2 Supported Engines

* MySQL
* PostgreSQL
* MariaDB
* Oracle
* SQL Server

---

### 10.3 RDS Use Case

Production databases run in private subnets with Multi-AZ for high availability.

---

## 11. EC2 Auto Scaling

### 11.1 What is Auto Scaling?

Automatically adjusts EC2 instance count based on demand.

---

### 11.2 Scaling Types

* Dynamic
* Manual
* Scheduled

---

### 11.3 Real World Use Case

E-commerce applications scale during sales and reduce capacity afterward.

---

## 12. IAM (Identity and Access Management)

### 12.1 What is IAM?

Controls access to AWS resources securely.

---

### 12.2 IAM Components

* Users
* Groups
* Roles
* Policies

---

### 12.3 Best Practices

* Avoid root account
* Enable MFA
* Use least privilege
* Prefer roles over credentials

---

## 13. S3 (Simple Storage Service)

### 13.1 What is S3?

Object storage service for storing and retrieving data at any scale.

---

### 13.2 Storage Classes

* Standard
* Intelligent Tiering
* Standard-IA
* Glacier
* Glacier Deep Archive

---

### 13.3 Use Cases

* Backup
* Static website hosting
* Media storage
* Log storage

---

## 14. Load Balancer

### 14.1 What is a Load Balancer?

Distributes traffic across multiple servers for availability and performance.

---

### 14.2 Types

* Application Load Balancer
* Network Load Balancer
* Gateway Load Balancer

---

### 14.3 Real World Use Case

Works with Auto Scaling to handle traffic spikes without downtime.















# AWS EC2 Launch and Terraform Provisioning

## Task Objective
- Learn AWS core concepts and Terraform  
- Launch an EC2 instance manually using AWS Console  
- Provision an EC2 instance using Terraform  
- Document the complete process  

---

## Part 1: Launching an EC2 Instance Manually (AWS Console)

### Steps Followed
1. Logged in to AWS Management Console  
2. Navigated to EC2 service  
3. Clicked on **Launch Instance**  
4. Selected **Amazon Linux 2 AMI**  
5. Chose instance type **t3.micro**  
6. Selected VPC and subnet  
7. Configured security group to allow SSH (Port 22)  
8. Created and selected a key pair  
9. Launched the instance  

---

### EC2 Instance Running (Manual Creation)

![EC2 Instance Running](images/ec2-instance-running.png)

**Details:**
- Instance State: Running  
- Instance Type: t3.micro  
- Public IPv4 Address assigned  
- VPC and Subnet configured
  
<img width="1901" height="639" alt="image" src="https://github.com/user-attachments/assets/ca72f39e-7816-49b7-a0bd-f4fda0a35802" />


---

## Part 2: Provisioning EC2 Using Terraform

# Terraform Configuration: EC2 Provisioning

This project demonstrates the automated provisioning of an **Amazon EC2 instance** using **Terraform**.

---

## 1. Configuration Overview (`main.tf`)

The following HCL (HashiCorp Configuration Language) code is used to define the infrastructure:

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "ap-south-1"
}

resource "aws_instance" "terraform_ec2" {
  ami           = "ami-0a1b648e2cd533174"
  instance_type = "t2.micro"

  tags = {
    Name = "Terraform-EC2"
  }
}

```

---

## 2. Explanation of Configuration


**`terraform` block**: Defines the required AWS provider and its version.


 
**`provider "aws"`**: Specifies the AWS region (**ap-south-1**) where the EC2 instance will be created.


 
**`resource "aws_instance"`**: The core block that creates the EC2 instance.


 
**`ami`**: The Amazon Machine Image (AMI) used as a template for the instance OS.


**`instance_type`**: Defines the CPU and memory; **t2.micro** is used here as it is Free Tier eligible.

 
**`tags`**: Used to assign a name ("Terraform-EC2") and identify the resource in the console.



---

## 3. Terraform Commands Used

To deploy this infrastructure, the following standard Terraform workflow is used:

1. **`terraform init`**: Initializes the working directory and downloads the necessary AWS provider plugins.
2. **`terraform validate`**: Checks the configuration files for syntax errors and internal consistency.
3. **`terraform plan`**: Generates an execution plan, showing exactly what resources will be created before any changes are made.
4. **`terraform apply`**: Executes the actions proposed in the plan to create the EC2 instance in the AWS Cloud.

---

## 4. Result
 
**Deployment**: The EC2 instance was successfully created using the automated Terraform script.

 
**Verification**: The instance is visible, active, and running within the **AWS EC2 Console**.



Would you like me to create a `.gitignore` file for this project to ensure your Terraform state files aren't accidentally uploaded to GitHub?
