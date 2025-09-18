
Hosting a Static Website on AWS
This repository demonstrates how to host a static website using a serverless and scalable architecture on Amazon Web Services (AWS). The solution leverages several key AWS services to ensure the website is fast, secure, and highly available.

Architecture Overview
The hosting setup follows a specific request flow, as shown in the diagram below:

Diagram of the AWS hosting architecture
<img width="1366" height="768" alt="hosting" src="https://github.com/user-attachments/assets/78e7ebeb-5861-4c34-9131-6f66494a984d" />

How It Works: The Request Flow
The process for a user accessing the website involves five main steps:

DNS Lookup (Route 53): When a user's browser requests the website (e.g., example.com), Route 53, AWS's DNS service, directs the traffic to CloudFront.

Access Website (HTTPS): The request arrives at CloudFront, which immediately establishes a secure connection using HTTPS.

Use SSL Certificate (ACM): To secure the connection, CloudFront uses an SSL certificate managed by AWS Certificate Manager (ACM).

Request from Origin (CloudFront): Acting as a Content Delivery Network (CDN), CloudFront first checks its cache for the requested content. If the content is not cached, it forwards the request to the origin, which is an S3 bucket.

Redirect Requests (S3): The request is received by a private S3 bucket that is configured to redirect all incoming traffic to a public S3 bucket. This public bucket is where the static website files are actually stored.

Key AWS Services Used
Amazon S3 (Simple Storage Service): Used for storing the static website files. A private S3 bucket handles redirects, while a separate public S3 bucket hosts the content.

Amazon CloudFront: Functions as a Content Delivery Network (CDN) that caches content and delivers it to users with low latency. It also enforces HTTPS and works with an SSL certificate to ensure secure connections.

Route 53: AWS's Domain Name System (DNS) service that routes user requests to the correct destination, in this case, the CloudFront distribution.

AWS Certificate Manager (ACM): Provides and manages the SSL certificate required to enable secure HTTPS connections for the website.
