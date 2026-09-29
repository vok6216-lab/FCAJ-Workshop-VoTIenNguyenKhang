---
title : "Configure API Gateway"
date : 2025-09-09
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

## Configure API Gateway

Now we'll create a REST API in API Gateway and connect it to our Lambda functions.

### Step 1: Create REST API

1. Go to **API Gateway** service
2. Click **Create API**
3. Choose **REST API** → **Build**
4. Choose **New API**
5. API name: `TaskManagementAPI`
6. Description: `Serverless REST API for Task Management`
7. Endpoint Type: **Regional**
8. Click **Create API**

### Step 2: Create Resources

1. In the API, you'll see a root resource `/`
2. Click **Actions** → **Create Resource**
3. Resource name: `tasks`
4. Resource path: `tasks`
5. Enable **API Gateway CORS**
6. Click **Create Resource**

### Step 3: Create Methods

#### Create POST Method (Create Task)

1. Select `/tasks` resource
2. Click **Actions** → **Create Method**
3. Select **POST** → Click checkmark
4. Integration type: **Lambda Function**
5. Lambda Region: Your region
6. Lambda Function: `createTask`
7. Enable **Use Lambda Proxy Integration**
8. Click **Save** → **OK** (when prompted to add permissions)

#### Create GET Method (List Tasks)

1. Select `/tasks` resource
2. Click **Actions** → **Create Method**
3. Select **GET** → Click checkmark
4. Integration type: **Lambda Function**
5. Lambda Function: `listTasks`
6. Enable **Use Lambda Proxy Integration**
7. Click **Save** → **OK**

#### Create GET Method (Get Single Task)

1. Select `/tasks` resource
2. Click **Actions** → **Create Resource**
3. Resource name: `{id}`
4. Resource path: `{id}`
5. Enable **API Gateway CORS**
6. Click **Create Resource**
7. Select `/tasks/{id}` resource
8. Create **GET** method → Connect to `getTask` function
9. Create **PUT** method → Connect to `updateTask` function
10. Create **DELETE** method → Connect to `deleteTask` function

### Step 4: Enable CORS

1. Select `/tasks` resource
2. Click **Actions** → **Enable CORS**
3. Accept default settings
4. Click **Enable CORS and replace existing CORS headers**

### Step 5: Deploy API

1. Click **Actions** → **Deploy API**
2. Deployment stage: **New Stage**
3. Stage name: `dev`
4. Stage description: `Development stage`
5. Click **Deploy**

### Step 6: Get API Endpoint

After deployment, you'll see the **Invoke URL**. This is your API endpoint.

Example: `https://abc123xyz.execute-api.us-east-1.amazonaws.com/dev`

### API Endpoints

Your API will have the following endpoints:

- `POST /tasks` - Create a new task
- `GET /tasks` - List all tasks
- `GET /tasks/{id}` - Get a specific task
- `PUT /tasks/{id}` - Update a task
- `DELETE /tasks/{id}` - Delete a task

### Testing the API

You can test the API using:

1. **API Gateway Console** - Use the "Test" feature
2. **Postman** - Import the API and test endpoints
3. **curl** - Use command line
4. **Browser** - For GET requests

### Example cURL Commands

```bash
# Create a task
curl -X POST https://your-api-id.execute-api.region.amazonaws.com/dev/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Learn AWS", "description": "Complete Lambda workshop", "status": "pending"}'

# List all tasks
curl https://your-api-id.execute-api.region.amazonaws.com/dev/tasks

# Get a specific task
curl https://your-api-id.execute-api.region.amazonaws.com/dev/tasks/{task-id}

# Update a task
curl -X PUT https://your-api-id.execute-api.region.amazonaws.com/dev/tasks/{task-id} \
  -H "Content-Type: application/json" \
  -d '{"title": "Updated title", "status": "completed"}'

# Delete a task
curl -X DELETE https://your-api-id.execute-api.region.amazonaws.com/dev/tasks/{task-id}
```

### Next Steps

Test your API thoroughly, then proceed to cleanup section to remove resources.
