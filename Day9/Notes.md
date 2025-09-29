# T A S K - 1.1 :

## D E S C R I P T I O N:

Your company is launching a new web application and requires a highly available and scalable infrastructure on AWS. 
The goal is to automatically handle traffic spikes by scaling EC2 instances up or down, distribute incoming traffic evenly across instances, and monitor the system's performance. Additionally, the system should notify the operations team via email when instances are added or removed based on CPU utilisation. Requirements:

  - Set up an EC2 instance running a web application that serves a "Hello World" page.
  - Set up an Auto Scaling Group (ASG) with a minimum of 1 and a maximum of 3 instances to manage EC2 instances for web traffic.
  - Create an Elastic Load Balancer (ELB) to evenly distribute incoming traffic.
  - Configure CloudWatch Alarms to monitor CPU utilisation for scaling events.
  - Scale out when CPU utilisation exceeds 70% for 5 minutes.
  - Scale in when CPU utilization drops below 30% for 5 minutes.
  - Ensure the infrastructure automatically scales to handle varying traffic loads.

<hr />

## S T E P S 
  - Launched 2 instances with user data as follows (created this as a template too) :
    ```
    #!/bin/bash
    yum update -y
    yum install -y httpd
    systemctl start httpd
    systemctl enable httpd
    echo "Hello World from $(hostname -f)" > /var/www/html/index.html

    ```
    <img src="https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day9/EC2.png" />
  ## Created Target group
    <img src="https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day9/TargetGroup.png" />
  ## Created Load balancer
    <img src="https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day9/ALB.png" />
  ## Created Auto Scaling Group with this template, and attached the Load balancer to this
    <img src="https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day9/ASG.png" />
  ## Created two alarms `scale out` and `scale in` and attached it to two new **step-scaling** policies in **ASG**
    <img src="https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day9/Choosing%20CPU%20Utilization.png" />
    <img src="https://github.com/Shamlin-Presidio/AWS_Training/blob/main/Day9/Policy%20in%20ASG.png" />
