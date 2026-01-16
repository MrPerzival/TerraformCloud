Cloud Infrastructure
This project demonstrates a cloud infrastructure setup using AWS and Terraform, hosting a Next.js application with load balancing capabilities.

Architecture Overview
The infrastructure consists of:

2 EC2 instances running the Next.js application
Elastic Load Balancer (ELB) for traffic distribution
Security groups for both EC2 instances and ELB
CI/CD pipeline using GitHub Actions
Prerequisites
AWS Account
AWS CLI configured
Terraform (v1.5.0 or later)
Node.js (v18 or later)
Docker
GitHub account (for CI/CD)
Project Structure
TerraformCloud/
├── main.tf
├── provider.tf           # AWS provider and resource configurations
├── variables.tf         
├── frontend/            # Next.js application
└── .github/workflows/   # CI/CD configuration
Infrastructure Details
AWS Resources
Region: ap-south-1
Instance Type: t2.micro
AMI: ami-00bb6a80f01f03502 (Ubuntu)
Load Balancer: Classic ELB with cross-zone load balancing
Security Groups:
EC2: Ports 80, 22, 3000
ELB: Port 80
Security Groups Configuration
EC2 instances allow incoming traffic on ports:
80 (HTTP)
22 (SSH)
3000 (Next.js development)
ELB allows incoming traffic on port 80
Next.js Application
Deployment
Manual Deployment
Initialize Terraform:
terraform init
Apply Terraform configuration:
terraform apply
Build and run the Next.js application:
cd frontend
npm install
npm run build
npm start
Automated Deployment (CI/CD)
The project includes a GitHub Actions workflow that:

Checks out the repository
Sets up Terraform
Initializes and applies Terraform configuration
Requires AWS credentials as GitHub secrets:
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
Environment Variables
Required environment variables for the frontend:

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY
CLERK_SECRET_KEY
Development
Clone the repository:
git clone <repository-url>
Install frontend dependencies:
cd frontend
npm install
Run development server:
npm run dev
Access the application at http://localhost:3000
Docker Support
The frontend includes a Dockerfile for containerization:

cd frontend
docker build -t frontend .
docker run -p 3000:3000 frontend
Security Notes
Ensure to keep your AWS credentials secure
Never commit .env files containing sensitive data
Update security group rules according to your production needs
Regularly update dependencies for security patches
