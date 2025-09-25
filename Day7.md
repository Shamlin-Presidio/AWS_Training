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
  - Created ALB and conected to my VPC and used it as CNAME, just as in Course
    ` We were told to skip Domain registration and certification for the same, but I just explored ACM for the same`
    

## INDIVIDUAL CACHING:
  - Created custom cache policy with Min TTL: 0, Default TTL: 3600, Max TTL: 86400
  - Used this policy in na new behaviour for the path `/images`

## NOTES:
  - CDN delivers content from edge locations closer to users, reducing latency
  - Enable CloudWatch metrics and access logs.
  - We can create and use policies for optimal TTL Values, behaviours etc.
  - Cache stratergy: invlidation can be done by using shorter TTLs for dynamic files/content

<hr />


# T A S K - 2
## DESCRIPTION:

As an AWS Cloud Engineer managing a global e-commerce platform, you need to ensure low latency, high availability, and fault tolerance using AWS Route 53 for DNS management and traffic routing.
## **Requirements:**
<br />
DNS Management: Configure Route 53 hosted zones to manage domain and subdomain records (e.g., A/AAAA records for EC2 or load balancers). 
<br />
**Routing Policies:**
<br />
**Latency-Based:** Route users to the nearest AWS region for the lowest latency. <br />
**Weighted:** Distribute traffic across multiple resources with adjustable weights. <br />
**Failover:** Redirect traffic to a backup resource if the primary fails using health checks.<br />
**Geolocation:** Direct users to region-specific endpoints (e.g., EU users to EU servers).<br />
**Health Checks:** Monitor backend services and reroute traffic from unhealthy resources.<br />
