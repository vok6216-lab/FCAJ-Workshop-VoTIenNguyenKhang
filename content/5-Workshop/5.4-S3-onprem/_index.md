---
title : "Create Lambda Functions"
date : 2025-09-09
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

## Create Lambda Functions

We'll create Lambda functions to handle CRUD operations for our tasks API.

### Step 1: Create IAM Role for Lambda

First, we need to create an IAM role that allows Lambda to access DynamoDB.

1. Go to **IAM** service in AWS Console
2. Click **Roles** → **Create role**
3. Select **AWS service** → **Lambda**
4. Click **Next**
5. Attach policy: **AmazonDynamoDBFullAccess** (for this workshop)
6. Role name: `lambda-dynamodb-role`
7. Click **Create role**

### Step 2: Create Lambda Function - Create Task

1. Go to **Lambda** service
2. Click **Create function**
3. Choose **Author from scratch**
4. Function name: `createTask`
5. Runtime: **Python 3.11**
6. Execution role: Use existing role → Select `lambda-dynamodb-role`
7. Click **Create function**

### Lambda Function Code - Create Task

Replace the default code with:

```python
import json
import boto3
import uuid
from datetime import datetime

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('tasks')

def lambda_handler(event, context):
    try:
        body = json.loads(event['body'])
        
        task = {
            'id': str(uuid.uuid4()),
            'title': body['title'],
            'description': body.get('description', ''),
            'status': body.get('status', 'pending'),
            'createdAt': datetime.utcnow().isoformat(),
            'updatedAt': datetime.utcnow().isoformat()
        }
        
        table.put_item(Item=task)
        
        return {
            'statusCode': 201,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps(task)
        }
    except Exception as e:
        return {
            'statusCode': 500,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps({'error': str(e)})
        }
```

### Step 3: Create Lambda Function - List Tasks

1. Create another function: `listTasks`
2. Same configuration as above
3. Use this code:

```python
import json
import boto3

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('tasks')

def lambda_handler(event, context):
    try:
        response = table.scan()
        tasks = response['Items']
        
        return {
            'statusCode': 200,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps(tasks)
        }
    except Exception as e:
        return {
            'statusCode': 500,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps({'error': str(e)})
        }
```

### Step 4: Create Lambda Function - Get Task

Function name: `getTask`

```python
import json
import boto3

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('tasks')

def lambda_handler(event, context):
    try:
        task_id = event['pathParameters']['id']
        
        response = table.get_item(Key={'id': task_id})
        
        if 'Item' not in response:
            return {
                'statusCode': 404,
                'headers': {
                    'Content-Type': 'application/json',
                    'Access-Control-Allow-Origin': '*'
                },
                'body': json.dumps({'error': 'Task not found'})
            }
        
        return {
            'statusCode': 200,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps(response['Item'])
        }
    except Exception as e:
        return {
            'statusCode': 500,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps({'error': str(e)})
        }
```

### Step 5: Create Lambda Function - Update Task

Function name: `updateTask`

```python
import json
import boto3
from datetime import datetime

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('tasks')

def lambda_handler(event, context):
    try:
        task_id = event['pathParameters']['id']
        body = json.loads(event['body'])
        
        # Get existing task
        response = table.get_item(Key={'id': task_id})
        
        if 'Item' not in response:
            return {
                'statusCode': 404,
                'headers': {
                    'Content-Type': 'application/json',
                    'Access-Control-Allow-Origin': '*'
                },
                'body': json.dumps({'error': 'Task not found'})
            }
        
        # Update task
        update_expression = "SET updatedAt = :updatedAt"
        expression_values = {
            ':updatedAt': datetime.utcnow().isoformat()
        }
        
        if 'title' in body:
            update_expression += ", title = :title"
            expression_values[':title'] = body['title']
        
        if 'description' in body:
            update_expression += ", description = :description"
            expression_values[':description'] = body['description']
        
        if 'status' in body:
            update_expression += ", #status = :status"
            expression_values[':status'] = body['status']
        
        table.update_item(
            Key={'id': task_id},
            UpdateExpression=update_expression,
            ExpressionAttributeValues=expression_values,
            ExpressionAttributeNames={'#status': 'status'},
            ReturnValues='ALL_NEW'
        )
        
        # Get updated task
        updated_response = table.get_item(Key={'id': task_id})
        
        return {
            'statusCode': 200,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps(updated_response['Item'])
        }
    except Exception as e:
        return {
            'statusCode': 500,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps({'error': str(e)})
        }
```

### Step 6: Create Lambda Function - Delete Task

Function name: `deleteTask`

```python
import json
import boto3

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('tasks')

def lambda_handler(event, context):
    try:
        task_id = event['pathParameters']['id']
        
        # Check if task exists
        response = table.get_item(Key={'id': task_id})
        
        if 'Item' not in response:
            return {
                'statusCode': 404,
                'headers': {
                    'Content-Type': 'application/json',
                    'Access-Control-Allow-Origin': '*'
                },
                'body': json.dumps({'error': 'Task not found'})
            }
        
        # Delete task
        table.delete_item(Key={'id': task_id})
        
        return {
            'statusCode': 200,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps({'message': 'Task deleted successfully'})
        }
    except Exception as e:
        return {
            'statusCode': 500,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
            'body': json.dumps({'error': str(e)})
        }
```

### Next Steps

Now that we have all Lambda functions created, we'll configure API Gateway to connect them together.
