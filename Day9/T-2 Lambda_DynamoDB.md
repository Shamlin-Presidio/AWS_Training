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
## L A M D A  -  F U N C T I O N S:
`Referred GPT for this section, learning boto3 now`
<hr />

## ProcessTextFileFunction : (added this as trigger)
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
## CODE:

```python
import boto3
import datetime

s3 = boto3.client('s3')
dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('shamlin-DocumentMetadata')

def lambda_handler(event, context):
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']
    
    response = s3.get_object(Bucket=bucket, Key=key)
    text = response['Body'].read().decode('utf-8')
    word_count = len(text.split())

    metadata = {
        'FileName': key,
        'Timestamp': datetime.datetime.utcnow().isoformat(),
        'WordCount': word_count
    }

    table.put_item(Item=metadata)

    updated_text = f"WordCount: {word_count}\nTimestamp: {metadata['Timestamp']}\n\n{text}"
    processed_key = key.replace('raw-documents/', 'processed/')
    
    s3.put_object(
        Bucket=bucket,
        Key=processed_key,
        Body=updated_text.encode('utf-8')
    )

    return {"status": "done", "wordCount": word_count}
```
## Similary, created ArchiveHandlerFunction and DeletionNotifierFunction and added them as event triggers in S3
