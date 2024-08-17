![Alt text](/Host_a_Static_Website_on_AWS.png)


# Static Website Hosting on AWS

This project demonstrates how to host a static HTML web app on AWS using a highly available and scalable architecture. The website is hosted on EC2 instances within a Virtual Private Cloud (VPC), utilizing AWS resources for security, reliability, and fault tolerance.

## Project Overview

The project is structured to achieve the following:

- **VPC Configuration**: A Virtual Private Cloud (VPC) was configured with both public and private subnets across two different availability zones to ensure high availability.
- **Internet Gateway**: An Internet Gateway was deployed to facilitate connectivity between VPC instances and the internet.
- **Security Groups**: Security Groups were established to act as a network firewall for controlling traffic.
- **Multi-AZ Deployment**: Leveraged two Availability Zones to enhance system reliability and fault tolerance.
- **Public Subnets**: Public subnets were used for infrastructure components such as the NAT Gateway and Application Load Balancer.
- **EC2 Instance Connect**: Implemented EC2 Instance Connect Endpoint for secure connections to resources within both public and private subnets.
- **Private Subnets**: Web servers (EC2 instances) were positioned within private subnets for enhanced security.
- **NAT Gateway**: Instances in both the private application and data subnets were enabled to access the internet via the NAT Gateway.
- **Website Hosting**: The website was hosted on EC2 instances.
- **Application Load Balancer**: Employed an Application Load Balancer and a target group to evenly distribute web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
- **Auto Scaling Group**: Used an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.
- **Version Control**: Web files were stored on GitHub for version control and collaboration.
- **Security**: Application communications were secured using AWS Certificate Manager.
- **Notifications**: Configured Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.
- **DNS Management**: Registered a domain name and set up DNS records using Route 53.

## Architecture Diagram

## Deployment Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
   
2. **Setup the EC2 Instances**:
   - SSH into your EC2 instance and switch to the root user:
     ```bash
     sudo su
     ```
   - Update all installed packages:
     ```bash
     yum update -y
     ```
   - Install Apache HTTP Server:
     ```bash
     yum install -y httpd
     ```
   - Change to the Apache web root directory:
     ```bash
     cd /var/www/html
     ```
   - Install Git:
     ```bash
     yum install git -y
     ```
   - Clone the project repository:
     ```bash
     git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
     ```
   - Copy all files to the Apache web root:
     ```bash
     cp -R host-a-static-website-on-aws/. /var/www/html/
     ```
   - Remove the cloned repository directory:
     ```bash
     rm -rf host-a-static-website-on-aws
     ```
   - Enable and start the Apache HTTP Server:
     ```bash
     systemctl enable httpd
     systemctl start httpd
     ``
     3. **Access the Website**:
   - Once the Apache server is running, the static website can be accessed through the public IP address of your EC2 instance or via the domain name registered with Route 53.

## Resources

- [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
- [EC2 Instance Connect Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Connect-using-EC2-Instance-Connect.html)
- [Auto Scaling Documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

