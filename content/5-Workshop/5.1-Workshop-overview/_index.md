---
title : "Introduction"
date :  2025-09-09 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

## Workshop Overview

### What is Serverless?

**Serverless computing** is a cloud computing model where the cloud provider manages the infrastructure, automatically provisioning, scaling, and managing servers. You only pay for the compute time you consume.

### Architecture Overview

In this workshop, we'll build a serverless REST API with the following architecture:

```
Client Request

    ↓

API Gateway (REST API)

    ↓

Lambda Function (Business Logic)

    ↓

DynamoDB (Data Storage)
```

### Components

#### 1. **Amazon API Gateway**

- Creates RESTful APIs
- Handles HTTP requests and responses
- Manages authentication and authorization
- Provides throttling and monitoring

#### 2. **AWS Lambda**

- Serverless compute service
- Executes code in response to events
- Automatically scales based on traffic
- Pay only for compute time used

#### 3. **Amazon DynamoDB**

- NoSQL database service
- Fully managed and serverless
- Fast and scalable
- Automatic scaling

### What We'll Build

A **Task Management API** with the following endpoints:

- `POST /tasks` - Create a new task
- `GET /tasks` - List all tasks
- `GET /tasks/{id}` - Get a specific task
- `PUT /tasks/{id}` - Update a task
- `DELETE /tasks/{id}` - Delete a task

### Benefits of Serverless Architecture

- **No server management** - AWS handles all infrastructure
- **Automatic scaling** - Handles traffic spikes automatically
- **Cost-effective** - Pay only for what you use
- **High availability** - Built-in redundancy and fault tolerance
- **Fast development** - Focus on code, not infrastructure
