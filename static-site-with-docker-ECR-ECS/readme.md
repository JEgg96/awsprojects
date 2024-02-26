##**Project Overview**

![1 _Docker](https://github.com/JEgg96/awsprojects/assets/150167799/ce161b14-0885-4ef6-93db-ecfa9489d192)



This readme provides an overview of the AWS project setup for a static website deployment using Docker, AWS ECS (Elastic Container Service), VPC (Virtual Private Cloud), Route 53, AWS Certificate Manager, and IAM (Identity and Access Management).

## Project Overview

The project involves deploying a static website on AWS using Docker containers. The steps include building a Docker container image, storing it in Docker Hub, setting up IAM user for programmatic access, configuring ECR (Elastic Container Registry), networking components like VPC, NAT Gateways, and Application Load Balancer, ECS cluster and task definition creation, domain setup in Route 53, SSL certificate registration with AWS Certificate Manager, and configuring HTTPS listener for the Application Load Balancer.

## Deployment Steps

1. **Build Docker Container Image:**
    - Create a Dockerfile in your project directory specifying the build steps for your static website.
    - Build the Docker image locally using the `docker build` command.
    - Tag the image appropriately for pushing to Docker Hub.
    ```bash
    docker build -t your-image-name .
    docker tag your-image-name your-dockerhub-username/your-image-name:tag
    ```

2. **Push Docker Image to Docker Hub:**
    - Log in to Docker Hub using `docker login`.
    - Push the Docker image to your Docker Hub repository.
    ```bash
    docker push your-dockerhub-username/your-image-name:tag
    ```

3. **Create IAM User for Programmatic Access:**
    - Log in to AWS Management Console.
    - Navigate to IAM and create a new user with programmatic access.
    - Attach policies granting necessary permissions for ECR, ECS, Route 53, ACM, etc.
    - Save the access key and secret key generated for this user securely.

4. **Configure IAM User's Credentials:**
    - Use the access key and secret key obtained in the previous step to authenticate programmatically with AWS services. This can be done by configuring AWS CLI or SDK in your deployment scripts.

5. **Create AWS ECR Repository:**
    - Log in to AWS Management Console.
    - Navigate to Amazon ECR and create a repository.
    - Tag your Docker image for pushing to ECR.
    ```bash
    docker tag your-image-name:tag aws-account-id.dkr.ecr.region.amazonaws.com/your-repo-name:tag
    ```
    - Push the Docker image to your ECR repository.
    ```bash
    docker push aws-account-id.dkr.ecr.region.amazonaws.com/your-repo-name:tag
    ```

6. **Setup Networking Components:**
    - Create a VPC with desired settings.
    - Create NAT Gateways for private subnet internet access.
    - Configure Security Groups for EC2 instances and Load Balancer.

7. **Create Application Load Balancer:**
    - Create an Application Load Balancer (ALB) in your VPC.
    - Configure listeners and target groups for routing traffic to ECS instances.

8. **Create ECS Cluster and Task Definition:**
    - Create an ECS cluster to manage container instances.
    - Define a task definition specifying your Docker image and resource requirements.
    - Configure task networking mode and container port mappings.

9. **Deploy ECS Service:**
    - Create a service within your ECS task definition.
    - Configure service settings like desired task count, deployment configuration, and load balancer integration.

10. **Domain Configuration and HTTPS Setup:**
    - Register a domain in Route 53 or use an existing one.
    - Create a record set pointing to your ALB.
    - Request an SSL certificate from AWS Certificate Manager for your domain.
    - Configure HTTPS listener on your ALB using the obtained SSL certificate.

## Deployment Scripts

You can automate these deployment steps using scripts. Below are example scripts for each step:

- `build_and_push_to_dockerhub.sh`: Script for building Docker image and pushing it to Docker Hub.
- `configure_iam_user_credentials.sh`: Script for configuring IAM user credentials programmatically.
- `push_to_ecr.sh`: Script for pushing Docker image to AWS ECR.
- `create_vpc_and_networking.sh`: Script for creating VPC, NAT Gateways, and configuring security groups.
- `create_alb_and_ecs.sh`: Script for creating ALB, ECS cluster, task definition, and service.
- `configure_domain_and_ssl.sh`: Script for configuring domain in Route 53 and setting up HTTPS with ACM.

## Note

- Make sure to replace placeholders like `your-image-name`, `your-dockerhub-username`, `your-repo-name`, etc., with your actual values.
- Ensure proper IAM permissions are set for the IAM user created in step 3.
- Securely manage IAM user credentials and avoid hardcoding them in scripts.
- Refer to AWS documentation for detailed instructions on each service setup and usage.

This README provides an overview of the deployment process for the AWS project. For detailed instructions and customization, refer to the respective AWS service documentation and sample scripts provided above.
