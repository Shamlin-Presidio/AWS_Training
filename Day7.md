# T A S K - 1 
## DESCRIPTION:
You are an AWS cloud engineer optimizing static content delivery for a global media streaming company. Your goal is to enhance performance and reduce latency by leveraging Amazon CloudFront as a CDN. <br />
Configure a CloudFront distribution to serve static assets from an S3 bucket or EC2 instance. 
<br />
Ensure S3 or Ec2 should be accessible only via CloudFront. <br />

**Test Delivery:** 
<br />
Test the CloudFront URL using tools like VPNs to confirm content is served from the nearest edge location.
<br />
**Optimize Caching:** 
<br />
Set cache behaviors with appropriate TTLs for different content types (e.g., longer for images, shorter for frequently updated files). 
<br />

## STEPS:
 - Created S3 bucket, added Index.html sample file
 - Created a cloudfront distribution, with the created S3 bucket as origin (Origin Access Control)

## GEO-RESTRICTION:
  - In Cloudfront, got to Security --> CloudFront geographic restrictions and added India and Singapore alone in allow list

## INDIVIDUAL CACHING:
  - Created custom cache policy with Min TTL: 0, Default TTL: 3600, Max TTL: 86400
  - Used this policy in na new behaviour for the path `/images`

## NOTES:
  - CDN delivers content from edge locations closer to users, reducing latency
  - Enable CloudWatch metrics and access logs.
  - We can create and use policies for optimal TTL Values, behaviours etc.
  - Cache stratergy: invlidation can be done by using shorter TTLs for dynamic files/content
