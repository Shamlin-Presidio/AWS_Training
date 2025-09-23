# Task Description:
Design and implement a resilient database infrastructure for a global trading platform operating in us-east-1 and eu-west-1.
## Requirements:
**Database Design:**
Deploy a secure and highly available database setup with multi-region capabilities. Database choice (Regional RDS)
Optimize performance and ensure compliance with data residency laws.
**Security:**
Manage and rotate database credentials securely.
Enable encryption for data at rest and in transit.
**Backup & Monitoring:**
Configure automated backups and enable detailed monitoring with alerts for critical metrics.
**Performance & Validation:**
Ensure low latency for users across regions.
Test failover, recovery, and performance under high transaction loads.
**Success Criteria:**
  - Secure credentials
  - low latency
  - zero data loss
  - seamless failover
  - effective monitoring
<hr/>

# Steps followed:

  - VPC already has 2 AZ's `us-east-1a` and `us-east-1b` each with 2 public and 2 private subnets in them
  - RDS: Chose Aurora --> More scalable, quick and efficient
  - Security: Chose AWS Secrets Manager (created a new key) for encryption
  - Enabled Key rotation for improved security
  - Monitoring and Backup enabled
  - Created alarm and new SNS topic for notifications
    ## Alarm Metric : CPU Utilization > 70

## ERROR: Not authorised to create RDS 
## Fix: changed it to serverless, then it worked!
