---
title : "Prerequisites and Setup"
date :  2025-09-09
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

## Prerequisites

### Required AWS Services Access

To complete this workshop, you need access to the following AWS services:

- AWS Lambda
- Amazon API Gateway
- Amazon DynamoDB
- AWS IAM
- Amazon CloudWatch Logs

### IAM Permissions

Your AWS account needs the following IAM permissions:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "lambda:*",
                "apigateway:*",
                "dynamodb:*",
                "iam:CreateRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy",
                "iam:GetRole",
                "iam:DeleteRole",
                "iam:DetachRolePolicy",
                "iam:DeleteRolePolicy",
                "logs:CreateLogGroup",
                "logs:DeleteLogGroup",
                "logs:DescribeLogGroups"
            ],
            "Resource": "*"
        }
    ]
}
```

### Software Requirements

- **AWS Account** with appropriate permissions
- **AWS Console Access** or **AWS CLI** configured
- Basic knowledge of **Python 3.x**
- Text editor or IDE (VS Code, PyCharm, etc.)

### AWS Region

We'll use **us-east-1 (N. Virginia)** for this workshop. You can choose any region, but make sure all resources are created in the same region.

## Setup Steps

### Step 1: Verify AWS Access

1. Log in to the AWS Management Console
2. Navigate to the AWS Lambda service
3. Ensure you can see the Lambda dashboard

### Step 2: Choose Your Region

1. Select your preferred AWS region from the top-right corner
2. Remember this region - all resources will be created here

### Step 3: Prepare Your Environment

- Have your text editor ready for writing Lambda function code
- Keep the AWS Console open in your browser
- Optionally, have AWS CLI configured if you prefer command-line tools

## Estimated Costs

This workshop uses AWS Free Tier eligible services:

- **Lambda**: 1M free requests per month
- **API Gateway**: 1M API calls per month for REST APIs
- **DynamoDB**: 25GB storage, 25 read/write capacity units

**Note**: If you exceed free tier limits, you may incur minimal charges. Always clean up resources after completing the workshop.
