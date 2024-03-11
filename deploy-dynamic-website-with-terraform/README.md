![1 Terraform-Ecommerce](https://github.com/JEgg96/awsprojects/assets/150167799/5c0c3b1d-a20a-4379-afa0-b5ee54c2f760)


# Terraform AWS E-commerce Website Deployment

Deploy an AWS infrastructure for your e-commerce website with ease using Terraform.

## Prerequisites 

Before you begin, ensure you have the following prerequisites installed:

- [Terraform](https://www.terraform.io/downloads.html)
- AWS CLI configured with appropriate permissions
- An existing AWS account

## Usage 

1. **Clone the repository**:

    ```bash
    git clone https://github.com/yourusername/ecommerce-terraform.git
    cd ecommerce-terraform
    ```

2. **Initialize Terraform**:

    ```bash
    terraform init
    ```

3. **Modify Terraform Variables (Optional)**: 

    Review and, if necessary, modify the `terraform.tfvars` file to customize deployment parameters such as AWS region, VPC CIDR blocks, etc.

4. **Apply Terraform Configuration**:

    ```bash
    terraform apply
    ```

5. **Note Terraform Outputs**:

    After successful deployment, Terraform will output the necessary information such as URLs, endpoint addresses, etc. Make sure to note them down for accessing your e-commerce website.

6. **Destroy Infrastructure (Optional)**:

    If needed, tear down the infrastructure by running:

    ```bash
    terraform destroy
    ```

## Terraform Scripts 

The `terraform` directory contains the following Terraform scripts:

- `main.tf`: Defines the AWS resources to be provisioned, including VPC, subnets, NAT gateways, security groups, RDS instance, SNS topic, autoscaling group, Route 53 record sets, etc.
- `variables.tf`: Declares the input variables used in the Terraform configuration.
- `outputs.tf`: Defines the output values to be displayed after successful deployment.

  

All Terraform scripts are available [here](https://github.com/JEgg96/terraform-projects).






