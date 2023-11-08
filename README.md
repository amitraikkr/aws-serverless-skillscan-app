<h1> AWS Serverless Application Resume & Job Description Analysis with OpenAI GPT-4</h1>

This serverless application uses AWS services, including Lambda, Amazon S3, DynamoDB, and the AWS Secret Manager, to analyze resumes and job descriptions. By leveraging the power of OpenAI's GPT-4, the service matches key skills and provides a compatibility percentage.

<h2>Features</h2>

Resume Analysis: Upload resume_userid.pdf to an S3 bucket, and our service will evaluate it against a job description.
User Interactions: Users can make up to 5 requests within a 24-hour period for interactive conversation with OpenAI's GPT-4.
Contextual Conversations: Utilizes DynamoDB for managing context in conversations with the OpenAI API.
Security: API keys are securely fetched from AWS Secret Manager.
Parameterization: Model and configuration parameters are managed via a parameters file for flexibility and customizability.

<h3>Prerequisites</h3>

Before you deploy the application, ensure you have the following:

AWS account with appropriate permissions for Lambda, S3, DynamoDB, and Secret Manager.
AWS SAM CLI installed and configured. Installation guide
OpenAI API key, stored securely in AWS Secret Manager.
Python 3.8 or later.
Git installed on your machine. Git Installation guide

<h2>Installation</h2>

git clone https://github.com/your-repo/resume-analysis-service.git
cd resume-analysis-service

Build the SAM application:

sam build

Deploy the application to your AWS account:

sam deploy --guided

Follow the prompts in the deploy process to set up the stack, including the S3 bucket name, DynamoDB table configuration, and secret names for API keys.

<h2>Usage</h2>

<h3>To use the application:<h3>

<p>
Upload the resume_userid.pdf to the designated S3 bucket.
<p>
Invoke the Lambda function via the AWS CLI or SDKs, passing the user ID and job description as event parameters.

{
  "userId": "user123",
  "jobDescription": "Your job description text here."
}

The Lambda function will interact with the OpenAI GPT-4 model to analyze the resume and job description, returning a percentage match and key skills analysis.

<h3>Throttling</h3>
Users are limited to 5 interactions with the OpenAI GPT-4 model within a 24-hour period. This is tracked using DynamoDB.

