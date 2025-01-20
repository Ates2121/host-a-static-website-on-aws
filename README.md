# Host a Static Website on AWS

This project showcases the process of hosting a static HTML web application on AWS. It involves deploying resources for scalability, fault tolerance, and security. Below is an overview of the resources and configurations used, along with instructions for setting up the environment.

## Project Features

### AWS Infrastructure Setup:
1. **Virtual Private Cloud (VPC):** Configured with both public and private subnets across two availability zones.
2. **Internet Gateway:** Deployed to enable connectivity between VPC instances and the internet.
3. **Security Groups:** Acted as a network firewall mechanism to regulate traffic.
4. **Availability Zones:** Leveraged two zones to enhance reliability and fault tolerance.
5. **Public Subnets:** Used for infrastructure components like the NAT Gateway and Application Load Balancer.
6. **Private Subnets:** Hosted web servers (EC2 instances) for enhanced security.
7. **NAT Gateway:** Allowed instances in private subnets to access the internet.
8. **EC2 Instance Connect Endpoint:** Enabled secure connections to both public and private subnets.

### Website Hosting:
1. **Web Servers:** Hosted the static HTML web app on EC2 instances within private subnets.
2. **Application Load Balancer:** Distributed traffic to an Auto Scaling Group of EC2 instances across multiple availability zones.
3. **Auto Scaling Group:** Ensured availability, scalability, and fault tolerance by automatically managing EC2 instances.
4. **Certificate Manager:** Secured application communications with SSL certificates.
5. **Simple Notification Service (SNS):** Configured to send alerts for activities in the Auto Scaling Group.
6. **Route 53:** Registered a domain name and configured DNS records.

### Version Control:
Web files were stored in a GitHub repository for version control and collaboration.

## Deployment Steps

### Bash Script for EC2 Instance Setup:
Use the following script to configure an EC2 instance for hosting the static website:

```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su

# Update all installed packages to their latest versions
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change the current working directory to the Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project GitHub repository to the current directory
git clone https://github.com/Ates2121/host-a-static-website-on-aws.git

# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws

# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd

# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

### Reference Diagram:
The repository includes a reference architecture diagram illustrating the AWS resource configuration. 

## Repository Contents
1. **Reference Diagram:** Visual representation of the AWS architecture.
2. **Bash Script:** Automates EC2 instance setup for hosting the static website.
3. **Static HTML Files:** Web application files.

## How to Use
1. Clone the GitHub repository to your local machine or EC2 instance:
   ```bash
   git clone https://github.com/Ates2121/host-a-static-website-on-aws.git
   ```
2. Follow the deployment steps outlined above to configure and host the website.
3. Use the provided architecture diagram to understand the setup and adapt it to your needs.

## Key Benefits
- High Availability: Leverages multiple availability zones and auto-scaling.
- Security: Ensures private hosting and controlled traffic.
- Scalability: Automatically adjusts to traffic demands.


### Repository Link
[GitHub Repository](https://github.com/Ates2121/host-a-static-website-on-aws)

## Conclusion
This project demonstrates the seamless deployment of a static website using AWS’s robust cloud infrastructure. By implementing best practices for security, scalability, and fault tolerance, it ensures a reliable and high-performing web hosting solution. Whether you are new to cloud technologies or looking to refine your skills, this project provides a comprehensive example of leveraging AWS resources effectively.

