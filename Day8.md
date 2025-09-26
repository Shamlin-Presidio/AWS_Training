# T A S K - 1
## DESCRIPTION:

You are an AWS cloud engineer tasked with deploying a containerized web application using Amazon ECS with EC2 launch type to handle varying traffic loads.

##
**Requirements:**

Deploy web application using ECS with EC2 instances

Set up an Application Load Balancer to distribute traffic.

Implement basic EC2 auto-scaling.

Monitor container health and log application events using CloudWatch.


## S T E P S :
  - Created Cluster with nnew ALB and an ASG in it
  - Created Task definition
  - Created a service using the task defintion
  - Manually increased the ECS tasks and then did ECS Auto scaling
  - New ASG for ECS EC2 instances and attached it to this cluster  ( CPU utlization>70% and also for <30% )
  - Container updates can be handled by registering a nenw version of the task (task definition) 
<hr />

# T A S K - 2
## DESCRIPTION:
You are a cloud engineer tasked in designing a notification system for an e-commerce platform to process and track orders.
##
**Requirements:**

Use SNS to send order confirmations to customers.

Use SQS to process order details in a separate queue.

Handle failed message delivery

Monitor queue performance

## 
## S T E P S :
  - Starting with **SQS**
  - Created 2 queues `orders` and `DLQ`. DLQ means Dead Letter Queue, learnt this from chatGPT and this is a queue to catch failed messages for retry/debug
  - Created **SNS topic**
  - Added the `orders` queue under the subscriptions
  - Started to poll for messages in SQS
  - Tested this by sending a message from SNS topic, and was able to recieve it in the SQS Queue
