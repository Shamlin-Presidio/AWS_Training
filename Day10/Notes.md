# D E S C R I P T I O N:

Create a CloudFormation template to deploy a scalable, secure web application on AWS with best practices. 
Develop separate AWS CloudFormation templates for each component of the application. Create a main CloudFormation template (e.g., main-stack.yaml) that references all the nested stack templates.

## Requirements: 
**Networking:**
    - Create a VPC with 2 public and 2 private subnets across AZs.
    - Add an Internet Gateway for public subnets and a NAT Gateway for private subnets.
    - Configure route tables for subnet associations.
**Compute:**
    - Deploy an Auto Scaling Group with EC2 instances in private subnets.
    - Use an ALB in public subnets to route traffic to EC2.
**Security:**
    - Add Security Groups for ALB, EC2.
    - Create an IAM role for EC2 with S3 and CloudWatch permissions.

## S T E P S :

I created the following yaml files in order:
    - networking.yaml
    - compute.yaml
    - security.yaml
    - main-stack.yaml
