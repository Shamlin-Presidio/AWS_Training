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

**1.** [networking.yaml](https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day10/networking.yaml)
**2.** [compute.yaml](https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day10/compute.yaml)
**3.** [security.yaml](https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day10/security.yaml)
**4.** [main-stack.yaml](https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day10/main-stack.yaml)

## And uploaded them, which gave individual s3 links annd I copied them to use in main-stack
```
https://s3.us-east-1.amazonaws.com/cf-templates-10u308snxiy7m-us-east-1/2025-10-03T110455.992Z03l-networking.yaml

https://s3.us-east-1.amazonaws.com/cf-templates-10u308snxiy7m-us-east-1/2025-10-03T110939.158Zikl-compute.yaml

https://s3.us-east-1.amazonaws.com/cf-templates-10u308snxiy7m-us-east-1/2025-10-03T111819.247Zifj-security.yaml

```
## O U T P U T:
<img src="https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day10/Assets/Final.png" />
