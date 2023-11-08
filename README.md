<h1> AWS Serverless Application Resume & Job Description Analysis with OpenAI GPT-4</h1>

This serverless application uses AWS services, including Lambda, Amazon S3, DynamoDB, and the AWS Secret Manager, to analyze resumes and job descriptions. By leveraging the power of OpenAI's GPT-4, the service matches key skills and provides a compatibility percentage.

<h2>Features</h2>

<ol>
  <li><strong>Resume Analysis</strong>: Upload <code>resume_userid.pdf</code> to an S3 bucket, and our service will evaluate it against a job description.</li>
  <li><strong>User Interactions</strong>: Users can make up to 5 requests within a 24-hour period for interactive conversation with OpenAI's GPT-4.</li>
  <li><strong>Contextual Conversations</strong>: Utilizes DynamoDB for managing context in conversations with the OpenAI API.</li>
  <li><strong>Security</strong>: API keys are securely fetched from AWS Secret Manager.</li>
  <li><strong>Parameterization</strong>: Model and configuration parameters are managed via a parameters file for flexibility and customizability.</li>
</ol>

<h3>Prerequisites</h3>

Before you deploy the application, ensure you have the following:

<ul>
  <li>AWS account with appropriate permissions for Lambda, S3, DynamoDB, and Secret Manager.</li>
  <li>AWS SAM CLI installed and configured. <a href="https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html" target="_blank">Installation guide</a></li>
  <li>OpenAI API key, stored securely in AWS Secret Manager.</li>
  <li>Python 3.8 or later.</li>
  <li>Git installed on your machine. <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git" target="_blank">Git Installation guide</a></li>
  <li>Create an AWS Secret Manager, save the OpenAI API Key, and update the template.yaml with Secret Manager ARN</li>
</ul>

<h2>Installation</h2>

git clone https://github.com/your-repo/resume-analysis-service.git
cd resume-analysis-service

Build the SAM application:

<b>sam build</b>

Deploy the application to your AWS account:

<b>sam deploy --guided</b>

Follow the prompts in the deploy process to set up the stack, create the AWS API Gateway REST API manually, and link with Lambda function.

<h2>Usage</h2>

<h3>To use the application:<h3>

<p>
Upload the resume_userid.pdf to the designated S3 bucket.
<p>
Invoke the Lambda function via the AWS CLI or SDKs, passing the user ID and job description as event parameters.

<b>{<br>
  "userId": "user123",<br>
  "jobDescription": "Your job description text here."<br>
}</b>

The Lambda function will interact with the OpenAI GPT-4 model to analyze the resume and job description, returning a percentage match and key skills analysis.

<h3>Throttling</h3>
Users are limited to 5 interactions with the OpenAI GPT-4 model within a 24-hour period. This is tracked using DynamoDB.

