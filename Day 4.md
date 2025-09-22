# TASK 1:

I have two subnets in my VPC in 2 AZs: `us-east-1a` and `us-east-1b`

Target Groups `tg-api` and `tg-web`

**ALB** with 2 Target groups with path based Targeting set as rules
  - api for `/api`
  - web for `web`

## ASG:
  - Creating two 2 **launch templates** for app(web) and api
  - Creating ASG for each service, and enabling **ELB and EBS Health check** 
  - Got `not authorized` 
<hr/>


# TASK 2:

Created New web template with httpd server
Stareted with **ASG**
Selected existing load balancer

## M E T R I C S:

Configured this in Scaling option and chose **Target tracking scaling policy**
  - `Metric`: Average CPU Utilization
  - `Target value`: 50% (standard)
  - `Cooldown period`: 300 seconds (default)
  - - Got `not authorized`, just as in prev step, not able to launch with any templates I create
