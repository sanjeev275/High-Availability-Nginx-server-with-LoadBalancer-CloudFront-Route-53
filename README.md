AWS High Availability Web Application with Nginx, Auto Scaling, ALB, CloudFront & Route 53
📌 Project Overview

This project demonstrates a highly available and scalable web application deployed on AWS. It leverages EC2 Auto Scaling, Application Load Balancer (ALB), Amazon CloudFront, and Route 53 for global DNS and CDN distribution. The application uses Nginx as a web server.

✅ Features

Highly Available Architecture: Multi-instance deployment using Auto Scaling.

Load Balancing: Distributes traffic using Application Load Balancer.

Global Content Delivery: Accelerated performance with CloudFront CDN.

Custom Domain Setup: Configured with Route 53 and SSL/TLS via ACM.

Scalable Infrastructure: Automatically scales EC2 instances based on demand.

Secure Communication: HTTPS enabled with AWS Certificate Manager.

🛠️ AWS Services Used

EC2 (Amazon Linux 2) – for hosting Nginx.

Auto Scaling Group – to manage EC2 instances.

Application Load Balancer (ALB) – to distribute traffic.

Amazon CloudFront – for caching and global distribution.

Route 53 – for DNS management.

AWS Certificate Manager (ACM) – for SSL/TLS.

📂 Project Architecture
User → Route 53 → CloudFront → Application Load Balancer → Auto Scaling Group → EC2 Instances (Nginx)

⚙️ Setup Instructions
1. Launch EC2 Instance & Install Nginx
sudo yum update -y
sudo amazon-linux-extras install nginx1 -y
sudo systemctl enable nginx
sudo systemctl start nginx

2. Create an AMI

Stop the EC2 instance → Create Image → Name it nginx-app-image.

3. Create Launch Template

Use the AMI created above.

Attach a Security Group allowing HTTP (80) and SSH (22).

4. Create Auto Scaling Group

Use the launch template.

Set Desired = 2, Min = 1, Max = 3.

Attach to Target Group for ALB.

5. Create Application Load Balancer

Add listener on Port 80.

Attach Target Group from Auto Scaling.

6. Configure CloudFront

Create distribution with:

Origin Domain: ALB DNS name.

Alternate Domain Name (CNAME): yourdomain.com.

SSL Certificate: Choose ACM certificate.

7. Configure Route 53

Create A Record (Alias) pointing to CloudFront distribution.

🌐 Access the Application

Using CloudFront domain:

https://<cloudfront-distribution>.cloudfront.net


Using custom domain:

https://yourdomain.com

📜 Architecture Diagram

(Add an image here showing EC2 → ALB → CloudFront → Route 53.)

📌 Future Enhancements

Implement CI/CD pipeline with Jenkins or GitHub Actions.

Add Monitoring & Alerts with CloudWatch.

Enable WAF & Shield for better security.

💻 Author

Sanju
Cloud & DevOps Enthusiast | AWS | Linux | Automation
