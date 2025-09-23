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


# FIX: Specified the instance type in template itself and retried for both tasks, It worked!

<hr/>

# TASK 3:

## STEPS:
  - created policy for S3 and cloudwatch access
  - created role for the same
  - Launched an instance
  - Tried aws s3 ls without IAM role, **FAILED**
  - Attached the Role, **Succeded**

### **OUTPUT:**
   ,     #_
   ~\_  ####_        Amazon Linux 2023
  ~~  \_#####\
  ~~     \###|
  ~~       \#/ ___   https://aws.amazon.com/linux/amazon-linux-2023
   ~~       V~' '->
    ~~~         /
      ~~._.   _/
         _/ _/
       _/m/'
[ec2-user@ip-10-0-0-93 ~]$ aws s3 ls

Unable to locate credentials. You can configure credentials by running "aws configure".
[ec2-user@ip-10-0-0-93 ~]$ aws s3 ls
2025-07-29 15:47:04 853973692277-bucket-state-file-karpenter
2025-05-25 21:00:43 amazon-sagemaker-853973692277-us-east-1-99709eed84c5
2024-10-16 12:57:33 appstream-app-settings-us-east-1-853973692277-slsiqk5l
2024-12-02 17:37:10 appstream-logs-us-east-1-853973692277-93mnax6y

## Creating Logs

  - Tried `aws logs create-log-group --log-group-name test-log-group`
  - gave the following error
  - Modified annd gave cloudwatch logs access
  - **Succeded**

[ec2-user@ip-10-0-0-93 ~]$ aws logs create-log-group --log-group-name test-log-group

An error occurred (AccessDeniedException) when calling the CreateLogGroup operation: User: arn:aws:sts::853973692277:assumed-role/EC2-S3_CloudWatch_Role/i-0d6e36e37fcaa2d16 is not authorized to perform: logs:CreateLogGroup on resource: arn:aws:logs:us-east-1:853973692277:log-group:test-log-group:log-stream: because no identity-based policy allows the logs:CreateLogGroup action
