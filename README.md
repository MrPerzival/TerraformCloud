InfraDeploy – Cloud Infrastructure on AWS

Overview
InfraDeploy demonstrates a complete cloud infrastructure setup using AWS and Terraform, hosting a Next.js application behind a load balancer with CI/CD automation. The project showcases real-world Infrastructure-as-Code (IaC), scalable architecture, and automated deployment practices.

Architecture Overview

The infrastructure consists of:

2 EC2 instances running a Next.js application

Elastic Load Balancer (ELB) for traffic distribution

Security Groups for EC2 instances and ELB

CI/CD pipeline using GitHub Actions

Request Flow:
User → Load Balancer → EC2 Instances → Next.js Application

Project Structure

TerraformCloud/
│
├── main.tf
├── provider.tf (AWS provider and resource configurations)
├── variables.tf (Input variables)
├── frontend/ (Next.js application)
│ ├── Dockerfile
│ └── ...
└── .github/workflows/ (CI/CD configuration)

Infrastructure Details

AWS Resources:

Region: ap-south-1

Instance Type: t2.micro

AMI: Ubuntu (ami-00bb6a80f01f03502)

Load Balancer: Classic ELB with cross-zone load balancing enabled

Security Groups:

EC2 Instances allow:

Port 80 (HTTP)

Port 22 (SSH)

Port 3000 (Next.js application)

ELB allows:

Port 80 (HTTP)

Prerequisites

AWS Account

AWS CLI configured

Terraform v1.5.0 or later

Node.js v18 or later

Docker

GitHub account (for CI/CD)

Deployment

Manual Deployment:

Initialize Terraform
terraform init

Apply Terraform configuration
terraform apply

Build and run the frontend
cd frontend
npm install
npm run build
npm start

Automated Deployment (CI/CD)

The project includes a GitHub Actions workflow that:

Checks out the repository

Sets up Terraform

Initializes and applies Terraform configuration

Deploys infrastructure automatically

Required GitHub Secrets:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

Environment Variables

Required environment variables for the frontend:

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY

CLERK_SECRET_KEY

Note: Store these in a .env file inside the frontend directory. Do not commit this file.

Development

Clone the repository:
git clone <repository-url>

Install dependencies:
cd frontend
npm install

Run development server:
npm run dev

Access the application at:
http://localhost:3000

Docker Support

The frontend includes Docker support.

Build the Docker image:
cd frontend
docker build -t frontend .

Run the container:
docker run -p 3000:3000 frontend

Security Notes

Keep AWS credentials secure

Never commit .env files

Restrict SSH access in production

Update security group rules based on production requirements

Regularly update dependencies for security patches

Key Learnings

Infrastructure-as-Code using Terraform

AWS EC2 and Load Balancing

CI/CD automation using GitHub Actions

Production-ready Next.js deployment

Cloud security best practices

Future Enhancements

Auto Scaling Groups

HTTPS using ACM and Route 53

Docker-based ECS or EKS deployment

Monitoring with AWS CloudWatch
