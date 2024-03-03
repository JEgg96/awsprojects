![How_to_Host_a_Dynamic_Web_App_on_AWS_with_Docker_Amazon_ECR_and_Amazon_ECS (1)](https://github.com/JEgg96/awsprojects/assets/150167799/9f4a4b66-45c5-4785-a3f3-c96dcd6ed87a)

# AWS Dynamic Web App Deployment Guide

This guide provides step-by-step instructions for deploying a dynamic web application on AWS using Docker, AWS Elastic Container Service (ECS), Virtual Private Cloud (VPC), Route 53, AWS Certificate Manager (ACM), and other AWS services. Additionally, deployment scripts are included to automate the deployment process.

## Prerequisites
Before proceeding, ensure you have the following:

- An AWS account
- Docker installed locally
- AWS CLI configured with appropriate permissions
- Basic understanding of AWS services

## Steps

### 1. Build and Push Docker Image
- Build a Docker container image for your web application.
- Create a repository in Docker Hub and push the image to this repository.
- Ensure you have Docker installed and configured properly.

**Deployment Script:**
```bash
# Build Docker image
docker build -t <your-image-name> .

# Login to Docker Hub
docker login

# Tag and push the image to Docker Hub
docker tag <your-image-name> <docker-hub-username>/<repository-name>:<tag>
docker push <docker-hub-username>/<repository-name>:<tag>
```

### 2. Create ECR Repository and Push Image
- Create an Amazon Elastic Container Registry (ECR) repository to store your Docker image.
- Push the Docker image from Docker Hub to the ECR repository.

**Deployment Script:**
```bash
# Create ECR repository
aws ecr create-repository --repository-name <repository-name>

# Tag the Docker image for ECR
docker tag <docker-hub-username>/<repository-name>:<tag> <aws-account-id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:<tag>

# Login to ECR
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <aws-account-id>.dkr.ecr.<region>.amazonaws.com

# Push the Docker image to ECR
docker push <aws-account-id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:<tag>
```

### 3. Set Up AWS Infrastructure
- Create a three-tier AWS network using Virtual Private Cloud (VPC), NAT gateways, and an Application Load Balancer (ALB).
- Create an ECS cluster and a task definition with the necessary configurations for your web application.
- Set up Route 53 domain and create a record set.
- Register for an SSL certificate in AWS Certificate Manager (ACM).
- Create an S3 bucket to store environment variables file.
- Use an IAM Role for the ECS task definition.

**Deployment Script:**
```bash
# Use AWS CloudFormation or AWS Management Console to set up VPC, ALB, ECS cluster, Route 53, ACM, and S3 bucket.
# Configure IAM Role for ECS task definition via AWS Management Console or AWS CLI.
```

### 4. Deploy Web Application
- Deploy the ECS service using the task definition created in the previous step.
- Create an HTTPS listener for the ALB to make the site secure.
- Configure environment variables for the ECS service using the S3 bucket.
- Associate the Route 53 domain with the ALB.

**Deployment Script:**
```bash
# Use AWS CLI or AWS Management Console to deploy ECS service.
# Configure HTTPS listener for ALB via AWS Management Console or AWS CLI.
# Set up environment variables for ECS service using AWS CLI or AWS SDK.
# Associate Route 53 domain with ALB using AWS CLI or AWS Management Console.
```

## Conclusion
By following these steps and using the provided deployment scripts, you can deploy your dynamic web application on AWS efficiently. Make sure to customize the scripts and configurations according to your specific application requirements and preferences. Happy deploying!
