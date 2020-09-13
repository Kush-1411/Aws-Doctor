# Aws-Doctor

Problem :-

As we have seen the a big problem in front of us  is a corona virus and we have seen that the people who are suffering from other diseases can’t get a regular check up who have a regular check up of their medical problem like kidney and heart because of lockdown or the social distancing the doctors are only attend the patients who have corona , rest of the people who do not have corona but have other diseases can’t get a proper treatment . Even can properly consult .


Solution :- 

To provide  the right advice and medicine from reports as well as an intelligent chatbot name doctor is used to provide a recommendation and in an emergency a call with a doctor but you have to fix your slot . You have to just scanned your documents and you get a desired result as well as a real time doctor solution and you can use speech  as well as text with our chatbots and many other features .


Technology :-

Serverless application for using Amazon Textract, AWS Amplify, Amazon API Gateway, AWS Lambda, Amazon S3, Amazon Cognito, and Amazon DynamoDB to create a document scanner application. Users can register, login, create projects, and upload images of text and generate a downloadable PDF of the detected text.
For doctor chatbot amazon lex , amazon polly , amazon s3 ,amazon lambda ,amazon api gateway.team


The full guide can be found on the AWS Compute Blog https://aws.amazon.com/blogs/compute/building-a-serverless-document-scanner-using-amazon-textract-and-aws-amplify/

An example serverless application for using Amazon Textract, AWS Amplify, Amazon API Gateway, AWS Lambda, Amazon S3, Amazon Cognito, and Amazon DynamoDB to create a document scanner application. Users can register, login, create projects, and upload images of text and generate a downloadable PDF of the detected text.
Frontend

    Follow the instructions to install and configure the Amplify CLI.
    Clone this project from GitHub and navigate to the amplify-frontend directory.

git clone https://github.com/Kush-1411/Aws-Doctor.git
cd Aws-Doctor/amplify-frontend

    Install the dependencies.

npm install

    Initialize Amplify in the project using this command. Follow the prompts.

amplify init

    Use Amplify to deploy the backend resources using AWS CloudFormation.

amplify push

Services Flow :- 

![20200904_111814](https://user-images.githubusercontent.com/69034923/93019095-83c77880-f5f2-11ea-9f05-6b9d4157a727.png)


Deploy the backend

The Serverless Application Model Command Line Interface (SAM CLI) is an extension of the AWS CLI that adds functionality for building and testing Lambda applications. It uses Docker to run your functions in an Amazon Linux environment that matches Lambda. It can also emulate your application's build environment and API.

To use the SAM CLI, you need the following tools.

    SAM CLI - Install the SAM CLI
    Node.js - Install Node.js 10, including the NPM package management tool.
    Docker - Install Docker community edition

To build and deploy your application for the first time, run the following in your shell from the serverless-backend/ directory:

sam build
sam deploy --guided

The first command will build the source of your application. The second command will package and deploy your application to AWS, with a series of prompts. You'll be asked for the UserPoolID and AmplifyStackName created by the Amplify CLI. Those values can be found in the amplify-frontend/amplify/backend/amplify-meta.json file generated by Amplify.

Once deployed, the SAM cli will output an API Endpoint. Create a file, api-config.js in the amplify-frontend/src/ directory with the endpoint:

const apiConfig = {
    "endpoint": "<ENDPOINT>",
    "s3_bucket_name": "<BucketName>",
    "s3_region": "<S3 REGION>"
};

export default apiConfig;

Run the frontend application

To run the application locally, enter this command from the amplify-frontend/ directory:

npm run serve

To publish the frontend to AWS cloud hosting:

amplify publish



After scanning get a real time solution using chatbot name aws-doctor , It shows you how to use AWS AI services to automate text data processing and insight discovery. With AWS AI services such as Amazon Textract, Amazon Comprehend and Amazon Lex, you can set up an automated serverless solution to address this requirement. We will walk you through below steps:

    Extract text from reports pdf or images with Amazon Textract.
    Derive insights with Amazon Comprehend.
    Interact with these insights in natural language using Amazon Lex.

Services Used
Deriving conversational insights from invoices with Amazon Textract, Amazon Comprehend, and Amazon Lex

This sample is based on the blog post (Link to be specified). It shows you how to use AWS AI services to automate text data processing and insight discovery. With AWS AI services such as Amazon Textract, Amazon Comprehend and Amazon Lex, you can set up an automated serverless solution to address this requirement. We will walk you through below steps:

    Extract text from receipts or invoices in pdf or images with Amazon Textract.
    Derive insights with Amazon Comprehend.
    Interact with these insights in natural language using Amazon Lex.

The following diagram illustrates the architecture of the solution:-
<img width="914" alt="arch" src="https://user-images.githubusercontent.com/69034923/93021162-ea529380-f5fe-11ea-93e3-026427665d59.png">




 The backend user or administrator uses the AWS Management Console or AWS Command Line Interface (AWS CLI) to upload the PDF documents or images to an S3 bucket.

    The Amazon S3 upload triggers a AWS Lambda function.

    The Lambda function invokes an Amazon Textract StartDocumentTextDetection async API, which sets up an asynchronous job to detect text from the PDF you uploaded.

    Amazon Textract notifies Amazon Simple Notification Service (Amazon SNS) when text processing is complete.

    A second Lambda function gets the notification from SNS topic when the job is completed to detect text.

    Once the lambda is notified of job completion from Amazon SNS, it calls a Amazon Textract GetDocumentTextDetection async API to receive the result from asynchronous operation and loads the results into an S3 bucket.

    A Lambda function is used for fulfillment of the Amazon Lex intents. For a more detailed sequence of interactions please refer to the Building your chatbot step in “Deploying the Architecture with Cloudformation” section.

    Amazon Comprehend uses ML to find insights and relationships in text. The lambda function uses boto3 APIs that Amazon Comprehend provides for entity and key phrases detection. a. In response to the Bot’s welcome message, the user types “Show me the report summary”, this invokes the GetReportSummary Lex intent and the Lambda function uses the Amazon Comprehend DetectEntities API for fulfillment b. When the user types “Get me the report details”, this invokes the Get
    ReportDetails intent, Amazon Lex prompts the user to enter report details, and the Lambda function uses the Amazon Comprehend DetectEntities API to return the report Details message c. When the user types “Can you show me the report notes for ”, this invokes the GetReportNotes intent, and the Lambda function uses the Amazon Comprehend DetectKeyPhrases API to return comments associated with the report

    You deploy the Lexbot Web UI in your AWS Cloudformation template by using an existing CloudFormation stack as a nested stack. To download the stack, see Deploy a Web UI for Your Chatbot. This nested stack deploys a Lex Web UI, the webpage is served as a static website from an S3 bucket. The web UI uses Amazon Cognito to generate an access token for authentication and uses AWS CodeStar to set up a delivery pipeline.The end-users interact this chatbot web UI. Please refer to this AWS github repo if you need more details on how to setup a Web UI for your Amazon Lex chatbot 


    You deploy the Lexbot Web UI in your AWS Cloudformation template by using an existing CloudFormation stack as a nested stack. To download the stack, see Deploy a Web UI for Your Chatbot. This nested stack deploys a Lex Web UI, the webpage is served as a static website from an S3 bucket. The web UI uses Amazon Cognito to generate an access token for authentication and uses AWS CodeStar to set up a delivery pipeline.The end-users interact this chatbot web UI. Please refer to this AWS github repo if you need more details on how to setup a Web UI for your Amazon Lex chatbots - https://github.com/aws-samples/aws-lex-web-ui.


![launchstack](https://user-images.githubusercontent.com/69034923/93021210-1d952280-f5ff-11ea-9fa3-1da481781c1e.png)


