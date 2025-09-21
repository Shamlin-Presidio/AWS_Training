# TASK 1:
## Description: As an AWS Cloud Engineer for a growing e-commerce platform, you must ensure high availability, data durability, and cost efficiency for EC2 instances and EBS volumes.
## Requirements:
  - Deploy EC2 instances across multiple Availability Zones (AZs) for high availability.
  - Automate regular backups of EBS volumes to ensure data recovery.
  - Implement cost-control mechanisms to prevent excessive spending on EC2 and EBS services.

## STEPS:
  - Created two EC2 instances in two AZs (subnets)
  - Subnets had IGW already set (prev. task)
  - **Backups**: Used AWS Backup, Weekly setup, `starts every sat, 12:30 AM`
  - 
