
# Project Deployment Documentation

## Purpose
This is a documentation of how I deployed a web page using AWS EC2 with Apache 2 on Ubuntu. It aims to set up a web server environment and deploy my HTML, CSS, and image files, making my web page accessible via a public IP address.

## Prerequisites

- An AWS account with the necessary permissions to create and manage EC2 instances.
- Basic knowledge of using Git for version control.
- Familiarity with SSH for connecting to remote servers.
- A GitHub repository set up to store my project files.

### Steps

1. **Create GitHub Repository**
   - I create a new repository on GitHub to store my project files.
     ```bash
     $ git init
     $ git add .
     $ git commit -m "Initial commit"
     $ git remote add origin <repository_url>
     $ git push -u origin main
     ```

2. **AWS Setup**
   - I create an AWS account if not already done.
   - I configure an IAM user with appropriate permissions for EC2 instance management.

3. **Launch EC2 Instance**
   - I launch an Ubuntu EC2 instance with desired configurations (e.g., instance type, security groups).
     ```bash
     $ aws ec2 run-instances --image-id <image_id> --instance-type <instance_type> --key-name <key_name> --security-group-ids <security_group_ids> --subnet-id <subnet_id>
     ```

4. **SSH into EC2 Instance**
   - I connect to my EC2 instance using SSH.
     ```bash
     $ ssh -i <key.pem> ubuntu@<public_ip>
     ```

5. **Install Apache 2**
   - I install Apache 2 web server on the EC2 instance.
     ```bash
     $ sudo apt update
     $ sudo apt install apache2
     ```

6. **Clone GitHub Repository**
   - I clone my GitHub repository into the EC2 instance.
     ```bash
     $ git clone <repository_url>
     ```

7. **Deploy Web Files**
   - I move my project files (HTML, CSS, images, etc.) to the Apache web directory.
     ```bash
     $ sudo mv /path/to/my/project/* /var/www/html/
     ```

8. **Configure Apache 2**
   - I configure Apache to serve my web page correctly.
     - If necessary, I edit the Apache configuration files (`/etc/apache2/sites-available/000-default.conf`) to set up virtual hosts or customize server settings.
     - I restart Apache to apply changes.
       ```bash
       $ sudo systemctl restart apache2
       ```

9. **View the Deployed Site**
   - I access my web page through the public IP address of my EC2 instance in a web browser.
     ```
     http://<public_ip>
     ```

## Conclusion
My web page is now deployed and accessible via the configured EC2 instance and Apache web server.
