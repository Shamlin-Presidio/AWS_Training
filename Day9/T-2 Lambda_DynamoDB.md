# TASK 2
## D E S C R I P T I O N:

You're a cloud architect for a company that processes large volumes of text-based documents. 
The company uses Amazon S3 as its primary storage solution. 
Your task is to implement an automated system using S3 event-based triggers, Lambda functions, and DynamoDB 
to process and manage these documents efficiently.

## Requirements:

**Text Processing:**
  - When a new .txt file is uploaded to the raw-documents/ prefix:
  - Trigger a Lambda function to count the words in the document.
  - Store the word count and metadata (file name, upload timestamp) in a DynamoDB table called DocumentMetadata.
  - Save a processed version(with the metadata added in the file at the top) of the file to the processed/ prefix.
    
**Archiving:**
  - When an object in the active-content/ prefix is tagged with archive, trigger a Lambda function to:
  - Move the object to the archived/ prefix.
  - Log the operation in DynamoDB, including the timestamp and user (passed via metadata).

**Deletion Notification:**
When an object is deleted, trigger a Lambda function to:
Send a notification to an SNS topic with details like file name, prefix, deletion time, and user (if available).
Log the deletion event in the DynamoDB table.

<hr />

## S T E P S
<h3 />

## Created S3 Bucket with the mentioned folders and DynamoDB Table 
## L A M D A   F U N C T I O N S:

<hr />

## Policy

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "S3Access",
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": [
        "arn:aws:s3:::shamlin-text-bucket /raw-documents/*",
        "arn:aws:s3:::shamlin-text-bucket /processed/*"
      ]
    },
    {
      "Sid": "DynamoDBAccess",
      "Effect": "Allow",
      "Action": [
        "dynamodb:PutItem"
      ],
      "Resource": "arn:aws:dynamodb:us-east-1:853973692277:table/shamlin-DocumentMetadata"
    }
  ]
}
```
