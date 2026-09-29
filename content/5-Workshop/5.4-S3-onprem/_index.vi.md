---
title : "Tạo các hàm Lambda"
date : 2025-09-09
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

## Tạo các hàm Lambda

Chúng ta sẽ tạo các hàm Lambda để xử lý các thao tác CRUD cho API task của chúng ta.

### Bước 1: Tạo IAM Role cho Lambda

Đầu tiên, chúng ta cần tạo một IAM role cho phép Lambda truy cập DynamoDB.

1. Vào dịch vụ **IAM** trong AWS Console
2. Nhấp **Roles** → **Create role**
3. Chọn **AWS service** → **Lambda**
4. Nhấp **Next**
5. Đính kèm policy: **AmazonDynamoDBFullAccess** (cho workshop này)
6. Tên role: `lambda-dynamodb-role`
7. Nhấp **Create role**

### Bước 2: Tạo hàm Lambda - Create Task

1. Vào dịch vụ **Lambda**
2. Nhấp **Create function**
3. Chọn **Author from scratch**
4. Tên hàm: `createTask`
5. Runtime: **Python 3.11**
6. Execution role: Use existing role → Chọn `lambda-dynamodb-role`
7. Nhấp **Create function**

### Code hàm Lambda - Create Task

Thay thế code mặc định bằng:

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

### Bước 3: Tạo hàm Lambda - List Tasks

1. Tạo một hàm khác: `listTasks`
2. Cấu hình giống như trên
3. Sử dụng code này:

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

### Bước 4: Tạo hàm Lambda - Get Task

Tên hàm: `getTask`

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

### Bước 5: Tạo hàm Lambda - Update Task

Tên hàm: `updateTask`

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
        
        # Lấy task hiện có
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
        
        # Cập nhật task
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
        
        # Lấy task đã cập nhật
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

### Bước 6: Tạo hàm Lambda - Delete Task

Tên hàm: `deleteTask`

```python
import json
import boto3

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('tasks')

def lambda_handler(event, context):
    try:
        task_id = event['pathParameters']['id']
        
        # Kiểm tra xem task có tồn tại không
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
        
        # Xóa task
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

### Các bước tiếp theo

Bây giờ chúng ta đã tạo tất cả các hàm Lambda, chúng ta sẽ cấu hình API Gateway để kết nối chúng lại với nhau.
