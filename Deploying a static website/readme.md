![Alt text](/awsprojects/Deploying a static website/Host_a_Static_Website_on_AWS (1).png)


---

# README: Hosting a Static Website on AWS

This README provides an overview of the DevOps project for hosting a static HTML web app on AWS. Below are the steps and resources utilized to deploy the web app on an EC2 instance within a well-architected AWS environment.

## Project Overview
This project aims to host a static website on AWS, ensuring reliability, scalability, security, and fault tolerance. Key AWS services and configurations were employed to achieve these objectives.

## Project Components and Configurations

1. **Virtual Private Cloud (VPC)**:
   - Configured a VPC spanning multiple availability zones (AZs) for high availability and fault tolerance.
   - Utilized both public and private subnets across different AZs.

2. **Internet Gateway**:
   - Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider internet.

3. **Security Groups**:
   - Established security groups to serve as a network firewall mechanism, controlling inbound and outbound traffic to instances.

4. **Availability Zones**:
   - Leveraged multiple availability zones to enhance system reliability and fault tolerance.

5. **Subnets**:
   - Utilized public subnets for infrastructure components like the NAT Gateway and Application Load Balancer.
   - Positioned web servers (EC2 instances) within private subnets for enhanced security.

6. **EC2 Instance Connect Endpoint**:
   - Implemented EC2 Instance Connect Endpoint for secure connections to assets within both public and private subnets.

7. **NAT Gateway**:
   - Enabled instances in private subnets to access the internet via NAT Gateway.

8. **Website Hosting**:
   - Hosted the static website on EC2 instances within the private subnets.

9. **Application Load Balancer (ALB)**:
   - Employed an Application Load Balancer and a target group to evenly distribute web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.

10. **Auto Scaling Group (ASG)**:
    - Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

11. **Version Control**:
    - Stored web files on GitHub for version control and collaboration.

12. **Certificate Manager**:
    - Secured application communications using AWS Certificate Manager.

13. **Simple Notification Service (SNS)**:
    - Configured Simple Notification Service to alert about activities within the Auto Scaling Group.

14. **Domain Registration and DNS Setup**:
    - Registered the domain name and set up a DNS record using Route 53 for routing traffic to the hosted website.

## Repository Information
The reference diagram and deployment scripts used for this project are available in [the GitHub repository provided.](https://github.com/jegg96/awsprojects)

#Deployment Script
#!/bin/bash

# Update all installed packages to their latest versions
sudo yum update -y

# Install Apache HTTP Server
sudo yum install -y httpd

# Change the current working directory to the Apache web root
cd /var/www/html

# Install Git
sudo yum install git -y

# Clone the project GitHub repository to the current directory
sudo git clone https://github.com/jegg96/awsprojects

# Copy all files, including hidden ones, from the cloned repository to the Apache web root
sudo cp -R awsprojects/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
sudo rm -rf awsprojects

# Enable the Apache HTTP Server to start automatically at system boot
sudo systemctl enable httpd 

# Start the Apache HTTP Server to serve web content
sudo systemctl start httpd

## Conclusion
By following this README and utilizing the provided resources, users can effectively deploy a static website on AWS, ensuring high availability, scalability, security, and fault tolerance.
