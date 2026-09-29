---
title: "Blog 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Orchestrating document processing with AWS AppSync Events and Amazon Bedrock

by Mehdi Amrane on July 9, 2025 in Advanced (300), Amazon Bedrock, Amazon Cognito, AWS Amplify, AWS AppSync, AWS Lambda, AWS Step Functions, Serverless, Technical How-to Permalink Share

Many organizations implement intelligent document processing workflows to extract meaningful insights from an ever-increasing volume of unstructured content (such as insurance claims, loan applications, etc.). Traditionally, these processes require significant technical effort, as implementations often involve using multiple machine learning (ML) models and orchestrating complex workflows.

When organizations integrate these channels into customer-facing applications (such as web applications for customers to upload documents like insurance claims, loan approval documents, etc.), they aim to provide real-time insights to enhance end-user experience. These organizations also aim to operate and scale these workloads with minimal operational overhead and cost optimization. Additionally, these organizations need to implement common security measures such as identity and access management to ensure that only authenticated and authorized users are allowed to perform specific actions or access specific resources.

In this article, we introduce a solution that simplifies the creation of intelligent document processing workflows, with a web application that allows customers to upload files (documents and images) and gather insights from them (summarization, field extraction, and classification). This solution primarily uses serverless technology, including a websocket to receive real-time insights and provides many benefits, such as automatic scaling, built-in high availability, and a pay-per-use pricing model for cost optimization. The solution also includes an authentication layer and an authorization layer to manage identity and permissions.

## Solution overview

In this post, we provide an overview of how the solution works and then describe how to set up the solution with the following services:

- Amazon Bedrock and Amazon Bedrock Data Automation to summarize the content of uploaded files (documents or images) and generate insights from them.
- AWS Step Functions and AWS Lambda to orchestrate summarization and extraction operations, using Amazon Bedrock and Amazon Bedrock Data Automation.
- AWS AppSync Events to create a serverless websocket for the web application to receive summarization and extraction insights in real time.
- AWS Amplify to create and deploy the web application
- Amazon EventBridge to trigger the orchestration workflow (using AWS Step Functions and AWS Lambda) when a new file is uploaded
- Amazon Cognito to implement an identity platform (user directory management and authorization) for the web application.
- Amazon Simple Storage Service (Amazon S3) to store uploaded files (for processing by the processing pipeline) and assets related to the web application.

The solution architecture is illustrated in the following diagram:

**Step 1:** User authenticates with the web application (hosted on AWS Amplify).

**Step 2:** Amazon Cognito authenticates credentials. Then, the user is logged into the web application.

**Step 3a and 3b:**
- **Step 3a:** Web application (AWS Amplify) subscribes to AWS AppSync Events websocket.
- **Step 3b:** AWS AppSync Events websocket calls AWS Lambda authorizer to verify that the user is allowed to subscribe to the web socket.

**Step 4:** User uploads a file (document or image) through the web application.

**Step 5:** Web application (hosted on AWS Amplify) calls Amazon Cognito (identity pool) to verify that the user is allowed to upload files.

**Step 6:** File is uploaded to Amazon S3 bucket.

**Step 7a and 7b:** When receiving an Amazon S3 upload event (notifying that a file has been uploaded to the Amazon S3 bucket) in the default Amazon EventBridge bus, an Amazon EventBridge bus rule triggers AWS Step Functions state machine execution to start the orchestration workflow.

**Step 8 (Extract fields from file and classify file):**
- **Step 8a:** First AWS Lambda function launches a new Amazon Bedrock Automation task (this task extracts specific fields from the uploaded file and classifies it).
- **Step 8b:** After the task completes, results are stored in an Amazon S3 bucket.
- **Step 8c and 8d:** When receiving an Amazon S3 event (notifying that results have been stored in the Amazon S3 bucket) on the default Amazon EventBridge, an Amazon EventBridge bus rule triggers execution of an AWS Lambda function.
- **Step 8e:** An AWS Lambda function publishes results to the web socket.

**Step 9a and 9b:** Second AWS Lambda function sends a prompt to Amazon Bedrock foundation model (Sonnet 3) to request summarization in the stream of the uploaded file. AWS Lambda function publishes streaming data to the web socket.

After Step 8e and Step 9b, the user can now view summarization results and file extraction insights for the uploaded file in the web application.

## Prerequisites

To implement and set up this solution, you must have the following:

- AWS account
- Device with access to your AWS account with the following:
  - Python 3.12 installed (including pip)
  - Node.js 20.12.0 installed
- Model Access enabled to Claude 3 Sonnet model in Amazon Bedrock

**Note:** Deploying this solution will incur costs. Please review the pricing page of each AWS service used in this article for cost details. The operating costs of this solution primarily depend on:
- Number of documents (and size of each document)
- Number of active users

## Setting up Amazon Bedrock Data Automation

In this section, we set up an Amazon Bedrock Data Automation project and Amazon Bedrock blueprint.

A project includes a list of blueprints, and each blueprint defines fields to extract from different file types (such as documents or images). In this article, we will define a blueprint for driver's licenses.

Complete the following steps to create an Amazon Bedrock Data Automation project and a driver's license blueprint:

1. Clone the GitHub repository:
   ```
   git clone https://github.com/aws-samples/sample-create-idp-with-appsyncevents-and-amazonbedrock.git
   ```

2. Navigate to the `sample-create-idp-with-appsyncevents-and-amazonbedrock` folder:
   ```
   cd sample-create-idp-with-appsyncevents-and-amazonbedrock
   ```

3. Initialize the environment (prepare shell script files from the GitHub repository for use):
   ```
   chmod +x ./init-env.sh && source ./init-env.sh
   ```

4. Run the `setup-bda-project.sh` script to create an Amazon Bedrock Data Automation project and sample driver's license blueprint:
   ```
   ./setup-bda-project.sh
   ```

## Creating websocket and orchestration backend

In this section, we create the following resources:

- A user directory for web authentication and authorization, created using Amazon Cognito user pool. An Amazon Cognito identity pool is also created to authenticate that users are allowed to upload files through the web application.
- A websocket using AWS AppSync Events. This allows our web application to receive real-time updates for summarization and extraction results. An authorization layer is also created to protect the websocket from unauthorized users. This layer is implemented with a Lambda authorization function to verify that incoming requests include valid authorization information.
- A state machine using AWS Step Functions and AWS Lambda to orchestrate summarization and extraction operations from unstructured content
- Amazon S3 to store and encrypt AWS Lambda functions.

Complete the following steps to create the websocket and orchestration backend of the solution, using AWS CloudFormation:

1. Create the Amazon S3 buckets used by the solution by running the following script. These buckets will store files uploaded by users and code files of AWS Lambda functions used in this solution.
   ```
   cd $CURRENT_DIR/s3; ./create-s3-buckets.sh
   ```

2. Create Amazon Cognito user pool and identity pool by running the `create-cognito-userpool.sh` script:
   ```
   cd $CURRENT_DIR/cognito; ./create-cognito-userpool.sh
   ```

3. Create AWS AppSync Events web socket by running the following script:
   ```
   cd $CURRENT_DIR/appsync/; ./create-appsync-api.sh
   ```

4. Create AWS Step Functions state machine (including AWS Lambda functions) by running the following scripts:
   ```
   cd $CURRENT_DIR/orchestration/; ./create-orchestration.sh
   ```

## Configuring Amazon Cognito user pool

In this section, we will create a user in the Amazon Cognito user pool. This user will log into our web application.

Run the `create-cognito-testuser.sh` script command to create a user (make sure to provide your email address):
```
cd $CURRENT_DIR/cognito; ./create-cognito-testuser.sh #your-email-address#
```

After you create the user, you will receive an email with a temporary password in this format: "Your username is #your-email-address# and temporary password is #temporary-password#."

Please record these login credentials (email address and temporary password) for later use when testing the web application.

## Creating the web application

In this section, we build a web application using AWS Amplify and publish the application so it can be accessed through an endpoint URL.

Complete the following steps to create the web application:

1. Run the `create-webapp.sh` script to create the web application with AWS Amplify:
   ```
   cd $CURRENT_DIR/amplify/; ./create-webapp.sh
   ```

2. Run the `deploy.sh` script to deploy the web application:
   ```
   cd $CURRENT_DIR/amplify/amplify-idp; ./deploy.sh
   ```

The web application is now available for testing and a URL will be displayed, as shown in the screenshot below. Please note the URL for use in the next section.

## Testing the web application

In this section, we will test the web application and upload a file for processing:

1. Open the AWS Amplify application URL in your web browser.
2. Enter login credentials (email and temporary password you received earlier when configuring the user pool in Amazon Cognito) and select Sign in.
3. When prompted, enter a new password and select Change password.
4. You can now see the web interface.
5. Download a sample driver's license at this location and upload it through the web application using your camera or a file from your local device, as illustrated.
6. After the file is uploaded, you will start receiving feedback in the web application. When all operations are complete, you will see results equivalent to the following screenshot:

**Note:** If you intend to use other sample driver's license images with different formats, you may need to update the existing Bedrock Data Automation blueprint we created earlier or define a new blueprint in the Bedrock Data Automation project we created earlier for these new images to work. For more information, please see Bedrock Data Automation documentation.

## Cleanup

To ensure no additional costs are incurred, delete the resources that have been provisioned in your account. Make sure you are using the correct AWS account before deleting the following resources.

**Important Note:** You should be careful when performing the steps above. Make sure you are deleting resources in the correct AWS account.

You can navigate to the AWS CloudFormation console to delete CloudFormation stacks associated with the provisioned resources or use the cleanup helper script `cleanup.sh` available at the root of the `sample-create-idp-with-appsyncevents-and-amazonbedrock` directory:
```
./cleanup.sh #region#
```

## Conclusion

In this article, we introduced a solution for creating document processing workflows, with a web application using serverless services. Through the web application, we can upload files and receive real-time feedback for different types of operations (summarization, extraction of specific fields, and classification). First, we created an Amazon Bedrock Data Automation project (with a driver's license blueprint). Then, we created a web socket along with an orchestration solution using a state machine (AWS Step Functions and AWS Lambda functions). We also configured a user pool to grant users access to the web application. Finally, we created the user interface (frontend) of the web application on AWS Amplify.

To dive deeper into this solution, a self-paced workshop is available in AWS Workshop Studio.
