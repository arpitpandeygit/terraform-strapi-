

# Terraform + Strapi on AWS EC2

**Infrastructure as Code (IaC) Assignment**

---

## 📌 Objective

The objective of this task is to:

- Launch an **AWS EC2 instance manually**
    
- Provision an **AWS EC2 instance using Terraform (Infrastructure as Code)**
    
- Deploy a **Strapi application** on EC2
    
- Follow **DevOps / SRE best practices**
    
- Maintain a clean and modular repository structure
    

---

## 🧰 Tech Stack Used

- **AWS EC2**
    
- **Terraform**
    
- **Amazon Linux**
    
- **Strapi (Node.js based CMS)**
    
- **Git & GitHub**
    
- **Nginx**
    
- **SSH**
    

---

## 📂 Repository Structure

```
terraform-projects/
├── main.tf
├── provider.tf
├── variables.tf
├── outputs.tf
├── modules/
│   └── ec2/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── .gitignore
└── README.md
---
```

## 🔐 Security Best Practices Followed

- Terraform state files (`terraform.tfstate`, `terraform.tfstate.backup`) are excluded from version control
    
- SSH private keys (`.pem`) are never committed
    
- Sensitive values are managed via variables
    
- `.gitignore` is used to prevent accidental exposure of credentials
    

---

## 🧩 Part 1: Manual EC2 Setup (AWS Console)

### Step 1: Launch EC2 Instance

- Instance Type: `t2.micro`
    
- AMI: Amazon Linux
    
- Key Pair: Newly created key pair for SSH access
    
- Security Group:
    
    - SSH (22) – restricted to personal IP
        
    - HTTP (80) – open for public access
        

---

### Step 2: Connect to EC2 via SSH

`ssh -i <key-name>.pem ec2-user@<public-ip>`

---

### Step 3: Install Node.js

`curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash - sudo yum install -y nodejs node -v npm -v`

---

### Step 4: Install and Run Strapi

`npx create-strapi@latest my-strapi-app --quickstart`

- Strapi admin panel becomes available on port `1337`
    

---

## 🧩 Part 2: Terraform – EC2 Provisioning (IaC)

### Step 1: Configure AWS CLI (Local Machine)

`aws configure`

- AWS Access Key
    
- AWS Secret Key
    
- Default region
    
- Output format
    

---

### Step 2: Terraform Provider Configuration

`provider.tf`

`provider "aws" {   region = var.aws_region }`

---

### Step 3: Modular Terraform Design

- EC2 resource is implemented using a reusable **Terraform module**
    
- Inputs include:
    
    - AMI ID
        
    - Instance type
        
    - Key pair name
        
    - Security group
        
    - Subnet ID
        
- Outputs expose the EC2 public IP
    

This approach improves **reusability**, **readability**, and **scalability**.

---

### Step 4: Initialize Terraform

`terraform init`

---

### Step 5: Validate and Plan

`terraform plan`

---

### Step 6: Apply Infrastructure

`terraform apply`

---

### Step 7: Verify EC2 Instance

- EC2 instance is successfully created using Terraform
    
- Public IP is retrieved via Terraform outputs
    
- SSH access to the instance is verified
    

---

## 🧩 Part 3: Strapi Deployment on Terraform EC2

- SSH into the Terraform-provisioned EC2 instance
    
- Install Node.js
    
- Install and run Strapi using the CLI
    
- Verify Strapi admin panel is accessible
    

---

## 📤 GitHub Usage

- Infrastructure code is pushed using Git
    
- Proper commit messages are maintained
    
- Sensitive files are excluded via `.gitignore`
    

---

## ✅ Task Completion Summary

✔ Manual EC2 provisioning  
✔ Terraform-based EC2 provisioning  
✔ Modular Terraform structure  
✔ Strapi deployed successfully  
✔ Secure repository practices followed

---

## Author

**Arpit Pandey**  
