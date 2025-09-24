# T A S K   1
## D E S C R I P T I O N:
A large media company stores millions of video files in their cloud storage. They have the following requirements:
Files that haven't been accessed for 90 days should be automatically deleted to optimize storage costs
However, some files might be old but frequently accessed (like classic movies) - these should be preserved regardless of their age.
The solution should be automated and scalable.
There should be a way to track which files were deleted
The deletion process should be cost-effective and not impact the performance of active file access
Design a cloud-based solution that addresses these requirements. Your solution should minimize operational overhead while ensuring reliable file management.
## **Requirements:**
  - Explain your choice of services and their roles
  - Describe how files will be tracked for access pattern
  - Detail the automation process for identifying and deleting unused files
  - Discuss any potential challenges and how to address them
  - Consider cost optimization aspects of your solution

## S T E P S:

## APPROACH : 
  Enable versioning : Some movies may face criticism and edit some scenes and re-upload.
  Tagging videos as Keep: false --> This would would mean that we can delete them (non-classic), but since we use versioning, delete markers can't be deleted if we use tags
  So, now I have to folders:
  - `classic`
  - `non-classic`

## Services and Their Roles
| Service                            | Role                                                             |
| ---------------------------------- | ---------------------------------------------------------------- |
| **Amazon S3**                      | Stores all media files in `classic/` and `non-classic/` prefixes |
| **S3 Lifecycle Rules**             | Automatically deletes `non-classic/` files after 90 days         |
| **CloudTrail**                     | Logs all deletions, including those triggered by Lifecycle rules |


## **Automation Process for Deleting Unused Files**
1.	Files are uploaded to classic/ (manually preserved) or non-classic/ (deletable through rules)
2.	S3 lifecycle rule is scoped to non-classic/
3.	Lifecycle rule deletes objects in non-classic/ after 90 days
4.	CloudTrail logs all deletion actions for audit
5.	S3 Inventory/Access logs record object metadata and access patterns


## **This is how we save costs**
| Strategy                              | Benefit                                                      |
| ------------------------------------- | ------------------------------------------------------------ |
| **Delete stale files**                | Massive savings from removing unnecessary data               |
| **Use of prefixes** instead of Lambda | Saves Lambda costs and avoids complexity                     |
| **No Glacier unless needed**          | Glacier saves cost but adds complexity and retrieval latency |

  
<hr />  

# T A S K   2
## D E S C R I P T I O N:
You're a cloud engineer for a large research institution that stores massive amounts of scientific data in Amazon S3. The institution has recently faced issues with accidental deletions and needs to implement better data protection measures. Additionally, they frequently need to perform large-scale operations on their data sets.
The institution has a primary S3 bucket named "science-data-2024" containing terabytes of research data.
﻿﻿﻿Recently, a researcher accidentally deleted a folder containing crucial experiment results.
﻿﻿﻿The institution often needs to update metadata tags on millions of files based on new classification criteria.
## **Requirements:**
  - Implement a solution to protect against accidental deletions and allow easy recovery of deleted data
  - Set up a process to efficiently update metadata tags on millions of objects without downloading and re-uploading them
  - Implement S3 cross region replication for different buckets.Make sure it replicate existing and new objects
