

---

# Ecommerce Website AWS Project

This project showcases the creation of an ecommerce website on AWS infrastructure, incorporating various services such as VPCs, EC2, NAT Gateways, security groups, RDS, S3, IAM Role with S3 access policy, MySQL Workbench data import, Application Load Balancer, Route 53 domain registration, SSL certificate registration, HTTPS listener, environment file configuration, Auto Scaling Group, and creation of an AMI.

## Project Components:

1. **Virtual Private Cloud (VPC):**
   - Utilized VPC to isolate and secure the network resources of the ecommerce application.

2. **EC2 Instances:**
   - Deployed EC2 instances to host the ecommerce website and execute various server-side tasks.

3. **NAT Gateways:**
   - Configured NAT Gateways to allow private instances within the VPC to access the internet for updates and external services.

4. **Security Groups:**
   - Implemented security groups to control inbound and outbound traffic to instances, ensuring a secure environment.

5. **RDS (Relational Database Service):**
   - Utilized RDS for hosting the MySQL database required by the ecommerce application, ensuring scalability, reliability, and ease of management.

6. **S3 (Simple Storage Service):**
   - Used S3 to store static assets such as images, CSS, and JavaScript files for the ecommerce website.

7. **IAM Role with S3 Access Policy:**
   - Created an IAM Role with a policy granting necessary permissions to access S3 buckets for serving static content.

8. **MySQL Workbench Data Import:**
   - Imported dummy data into the MySQL database using MySQL Workbench to simulate ecommerce product data.

9. **Application Load Balancer (ALB):**
   - Configured an ALB to distribute incoming traffic across multiple targets, ensuring high availability and fault tolerance.

10. **Route 53 Domain Registration:**
    - Registered a domain using Route 53 to provide a memorable and branded URL for the ecommerce website.

11. **SSL Certificate Registration:**
    - Registered an SSL certificate to enable secure communication between clients and the website, ensuring data integrity and confidentiality.

12. **HTTPS Listener:**
    - Configured an HTTPS listener on the ALB to enforce secure communication over SSL/TLS protocol.

13. **Environment File Configuration:**
    - Updated the environment file with necessary configurations such as database connection details, API keys, etc.

14. **Auto Scaling Group:**
    - Created an Auto Scaling Group to automatically adjust the number of instances based on demand, ensuring optimal performance and cost efficiency.

15. **AMI Creation:**
    - Created an AMI (Amazon Machine Image) to capture the configured state of instances, providing a snapshot for replication or restoration.

## Deployment Script (SSH into EC2):

#1. Update EC2 instance
sudo su
sudo yum update -y

#2. Install Apache
sudo yum install -y httpd httpd-tools mod_ssl
sudo systemctl enable httpd 
sudo systemctl start httpd

#3. Install PHP 7.4
sudo amazon-linux-extras enable php7.4
sudo yum clean metadata
sudo yum install php php-common php-pear -y
sudo yum install php-{cgi,curl,mbstring,gd,mysqlnd,gettext,json,xml,fpm,intl,zip} -y

#4. Install MySQL 5.7
sudo rpm -Uvh https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
sudo yum install mysql-community-server -y
sudo systemctl enable mysqld
sudo systemctl start mysqld

#5. Set Permissions
sudo usermod -a -G apache ec2-user
sudo chown -R ec2-user:apache /var/www
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
sudo find /var/www -type f -exec sudo chmod 0664 {} \;

#6. Download the FleetCart zip from S3 to the HTML directory on the EC2 instance
sudo aws s3 sync s3://jegg96-web-files /var/www/html

#7. Unzip the FleetCart zip folder
cd /var/www/html
sudo unzip FleetCart.zip

#8. Move all the files and folders from the FleetCart directory to the HTML directory
sudo mv FleetCart/* /var/www/html

#9. Move all the hidden files from the FleetCart directory to the HTML directory
sudo mv FleetCart/.DS_Store /var/www/html
sudo mv FleetCart/.editorconfig /var/www/html
sudo mv FleetCart/.env /var/www/html
sudo mv FleetCart/.env.example /var/www/html
sudo mv FleetCart/.eslintignore /var/www/html
sudo mv FleetCart/.eslintrc /var/www/html
sudo mv FleetCart/.gitignore /var/www/html
sudo mv FleetCart/.htaccess /var/www/html
sudo mv FleetCart/.npmrc /var/www/html
sudo mv FleetCart/.php_cs /var/www/html
sudo mv FleetCart/.rtlcssrc /var/www/html

#10. Delete the FleetCart and FleetCart.zip folder
sudo rm -rf FleetCart FleetCart.zip

#11. Import Dummy Data
sudo aws s3 sync s3://jegg96-web-file-dummy-data /home/ec2-user
sudo unzip dummy.zip
sudo mv dummy/* /var/www/html/public
sudo mv -f dummy/.DS_Store /var/www/html/public
sudo rm -rf /var/www/html/storage/framework/cache/data/cache
sudo rm -rf dummy dummy.zip
chown apache:apache -R /var/www/html 
sudo service httpd restart
