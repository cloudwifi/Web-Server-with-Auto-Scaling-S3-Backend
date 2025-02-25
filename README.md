# Web-Server-with-Auto-Scaling-S3-Backend

 Explanation of the Infrastructure

This Terraform configuration sets up a highly available web server infrastructure with auto-scaling capabilities and S3 backend. Here's a breakdown of what each component does:

 Infrastructure Components

1. *Networking*:
   - VPC with public subnets across two availability zones
   - Internet Gateway for public internet access
   - Appropriate route tables and security groups

2. *Web Server Infrastructure*:
   - Launch Template with user-data script to install Apache on Ubuntu instances
   - Auto Scaling Group maintaining minimum 2 instances
   - Application Load Balancer to distribute traffic

3. *Storage*:
   - S3 bucket for storing static assets including the index.html file
   - S3 backend for Terraform state management

 How it Works

1. When deployed, Terraform creates the entire infrastructure defined in the configuration.
2. The Auto Scaling Group ensures at least 2 instances are running across different availability zones.
3. Each EC2 instance runs a user-data script that:
   - Installs Apache web server
   - Downloads the index.html from S3 bucket
   - Replaces placeholders with actual instance metadata
4. The ALB distributes incoming traffic to healthy instances.
5. The index.html is stored in S3 and downloaded by each instance at startup.

![terraform](https://github.com/user-attachments/assets/8ab20e7a-4ee5-41c2-8c0c-513842d6c2c3)


