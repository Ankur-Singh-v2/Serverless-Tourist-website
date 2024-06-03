Serverless Web Application
This is a serverless web application hosted on AWS using the following services:

Amazon S3
Amazon CloudFront
AWS Route 53
AWS Lambda
Amazon API Gateway
Amazon DynamoDB
Amazon SNS
Architecture
The architecture of this serverless web application is as follows:

Route 53:

Domain Management: AWS Route 53 is used to manage your domain names and DNS settings, ensuring that your web application can be accessed via a user-friendly URL.
CloudFront:

Content Delivery Network (CDN): Amazon CloudFront is used to distribute your web content globally with low latency and high transfer speeds. It caches the content stored in S3 and serves it to users.
S3 (Simple Storage Service):

Static Content Hosting: Amazon S3 is used to host your static web content (HTML, CSS, JavaScript, images, etc.). CloudFront fetches this content from S3 to deliver it to users.
API Gateway:

API Endpoint Management: Amazon API Gateway acts as the entry point for your application's backend. It handles all the API calls from the client, invoking Lambda functions to process these requests.
Lambda:

Serverless Compute: AWS Lambda is used to run your backend code without provisioning or managing servers. When a user submits the form, API Gateway triggers a Lambda function to process the form data.
DynamoDB:

Database: Amazon DynamoDB is used to store the form data. The Lambda function inserts the user-submitted data into a DynamoDB table for persistent storage.
SNS (Simple Notification Service):

Notifications: Amazon SNS is used to send email notifications. The Lambda function publishes a message to an SNS topic when a user submits the form, triggering an email notification to the admin.
Architectural Flow:
User Request:

The user accesses the web application via a custom domain managed by Route 53.
Content Delivery:

The user's request is routed through CloudFront, which serves static content from S3.
Form Submission:

When the user submits a form, the browser sends a request to API Gateway.
API Gateway:

API Gateway receives the form submission and invokes a Lambda function.
Lambda Function:

The Lambda function processes the form data. It saves the data to DynamoDB.
The Lambda function also publishes a message to an SNS topic.
SNS Notification:

SNS sends an email notification to the admin based on the message published by the Lambda function.
