# html-AWS-EC2

# Project Deployment Documentation

## Purpose
This document provides a step-by-step guide to deploy a web page using AWS EC2 with Apache 2 on Ubuntu. It aims to help you set up a web server environment and deploy your HTML, CSS, and image files, making your web page accessible via a public IP address.

## Prerequisites
Before starting, ensure you have:
- An AWS account with necessary permissions to create and manage EC2 instances.
- Basic knowledge of using Git for version control.
- Familiarity with SSH for connecting to remote servers.
- A GitHub repository set up to store your project files.

### Steps

1. **Create GitHub Repository**
   - Create a new repository on GitHub to store your project files.
     ```bash
     $ git init
     $ git add .
     $ git commit -m "Initial commit"
     $ git remote add origin <repository_url>
     $ git push -u origin main
     ```

2. **AWS Setup**
   - Create an AWS account if not already done.
   - Configure an IAM user with appropriate permissions for EC2 instance management.

3. **Launch EC2 Instance**
   - Launch an Ubuntu EC2 instance with desired configurations (e.g., instance type, security groups).
     ```bash
     $ aws ec2 run-instances --image-id <image_id> --instance-type <instance_type> --key-name <key_name> --security-group-ids <security_group_ids> --subnet-id <subnet_id>
     ```

4. **SSH into EC2 Instance**
   - Connect to your EC2 instance using SSH.
     ```bash
     $ ssh -i <key.pem> ubuntu@<public_ip>
     ```

5. **Install Apache 2**
   - Install Apache 2 web server on the EC2 instance.
     ```bash
     $ sudo apt update
     $ sudo apt install apache2
     ```

6. **Clone GitHub Repository**
   - Clone your GitHub repository into the EC2 instance.
     ```bash
     $ git clone <repository_url>
     ```

7. **Deploy Web Files**
   - Move your project files (HTML, CSS, images, etc.) to the Apache web directory.
     ```bash
     $ sudo mv /path/to/your/project/* /var/www/html/
     ```

8. **Configure Apache 2**
   - Configure Apache to serve your web page correctly.
     - If necessary, edit the Apache configuration files (`/etc/apache2/sites-available/000-default.conf`) to set up virtual hosts or customize server settings.
     - Restart Apache to apply changes.
       ```bash
       $ sudo systemctl restart apache2
       ```

9. **View the Deployed Site**
   - Access your web page through the public IP address of your EC2 instance in a web browser.
     ```
     http://<public_ip>
     ```

## Conclusion
Your web page is now deployed and accessible via the configured EC2 instance and Apache web server.
