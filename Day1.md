# TASK 1:
  - Create resources required for each department
  - Create Policies for each Department, and allow access only to the resources they need (principle of least privilege )
  - (this is done by copying the ARN of the resources and pasting them there)


# TASK 2:
  - Create `AccessS3andDynamoPolicy` with S3 and DynamoDB access
  - Create `AppRole` policy and add these in each other's trust relationship


# TASK 3:
  ## STEPS:
  - Enable AWS IAM Identity Center `(external Identity Provider)`
  - Connect to the College Database
  - Configure SCIM (System for Cross-domain Identity Management) to sync users and groups (faculty, students, etc.)
  - **Thus University users can log in to the AWS Console with their existing university credentials**

  ## Managing: 
  - Create groups/roles in Central Directory (college DB)
  - Create policies
  - Attach the needed policies to the groups
  - Allow MFA in IAM Identity center
