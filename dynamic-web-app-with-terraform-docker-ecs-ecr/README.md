# Deploy Dynamic Web App on AWS with Terraform, Docker, Amazon ECR, and ECS

This guide walks you through deploying a dynamic web application on Amazon Web Services (AWS) using Terraform, Docker, Amazon Elastic Container Registry (ECR), and Elastic Container Service (ECS).

## Prerequisites

Before starting, ensure you have the following prerequisites:

- AWS account
- Terraform installed locally
- Docker installed locally
- Basic understanding of AWS, Docker, and Terraform

## Steps

1. **Set up AWS credentials**:

   Ensure your AWS credentials are configured on your local machine. You can achieve this by setting environment variables or using AWS CLI `aws configure`.

2. **Clone the repository**:

   Clone the repository containing your web application code and Terraform configuration:

   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

3. **Dockerize your web application**:

   Create a Dockerfile in the root directory of your project to containerize your web application. Ensure you have a working Dockerfile that builds your application into a Docker image.

4. **Build and push Docker image to Amazon ECR**:

   Follow these steps to build and push your Docker image to Amazon ECR:

   ```bash
   # Login to ECR
   $(aws ecr get-login --no-include-email --region <your-region>)

   # Build Docker image
   docker build -t <your-image-name> .

   # Tag Docker image
   docker tag <your-image-name>:latest <your-ecr-repository-url>:latest

   # Push Docker image to ECR
   docker push <your-ecr-repository-url>:latest
   ```

5. **Terraform modules for infrastructure components**:

   This project utilizes Terraform modules for managing various AWS resources. Here's a list of Terraform modules created for different infrastructure components:
   
   - [NAT Gateway](https://github.com/JEgg96/terraform-modules/nat-gateway)
   - [VPC](https://github.com/JEgg96/terraform-modules/vpc)
   - [Security Groups](https://github.com/JEgg96/terraform-modules/security-groups)
   - [RDS (Relational Database Service)](https://github.com/JEgg96/terraform-modules/rds)
   - [Amazon Certificate Manager (ACM) for SSL certificate](https://github.com/JEgg96/terraform-modules/acm)
   - [Application Load Balancer (ALB)](https://github.com/JEgg96/terraform-modules/alb)
   - [Amazon S3](https://github.com/JEgg96/terraform-modules/s3)
   - [Task Execution Role](https://github.com/JEgg96/terraform-modules/task-execution-role)
   - [ECS Cluster](https://github.com/JEgg96/terraform-modules/ecs-cluster)
   - [ECS Task](https://github.com/JEgg96/terraform-modules/ecs-task)
   - [Task Definition](https://github.com/JEgg96/terraform-modules/task-definition)
   - [ECS Service](https://github.com/JEgg96/terraform-modules/ecs-service)
   - [ECS Auto Scaling Group](https://github.com/JEgg96/terraform-modules/ecs-auto-scaling-group)
   - [Route 53 (DNS service)](https://github.com/JEgg96/terraform-modules/route53)
   - [DNS record for the application](https://github.com/JEgg96/terraform-modules/dns-record)

6. **Initialize Terraform and deploy infrastructure**:

   Initialize Terraform in your project directory and deploy the infrastructure:

   ```bash
   terraform init
   terraform apply
   ```

   Follow the prompts to review and confirm the Terraform execution plan.

7. **Access your web application**:

   Once Terraform has successfully deployed the infrastructure, you can access your web application using the ECS service URL or the public IP address of the EC2 instance running your application.

## Cleanup

To avoid incurring unnecessary charges, don't forget to destroy the Terraform-managed infrastructure once you're done:

```bash
terraform destroy
```

Follow the prompts to confirm the destruction of resources.

All terraform modules made and used are on: https://github.com/JEgg96/terrraform-modules

## Conclusion

By following these steps, you've successfully deployed a dynamic web application on AWS using Terraform, Docker, Amazon ECR, and ECS. Feel free to customize and expand upon this setup to suit your specific requirements.

---
