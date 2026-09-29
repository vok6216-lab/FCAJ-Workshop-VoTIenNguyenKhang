---
title : "Create DynamoDB Table"
date : 2025-09-09
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

## Create DynamoDB Table

DynamoDB is a NoSQL database that will store our tasks. Let's create a table to store task data.

### Step 1: Navigate to DynamoDB

1. Go to AWS Console
2. Search for "DynamoDB" in the services search bar
3. Click on **DynamoDB**

### Step 2: Create Table

1. Click **Create table** button
2. Configure the table:
   - **Table name**: `tasks`
   - **Partition key**: `id` (type: String)
   - **Table settings**: Use default settings
   - **Capacity mode**: On-demand (recommended for this workshop)

### Step 3: Create Table

1. Scroll down and click **Create table**
2. Wait for the table to be created (usually takes a few seconds)

### Table Structure

Our DynamoDB table will have the following structure:

- **id** (String) - Primary key - Unique identifier for each task
- **title** (String) - Task title
- **description** (String) - Task description  
- **status** (String) - Task status (e.g., "pending", "completed")
- **createdAt** (String) - Timestamp when task was created
- **updatedAt** (String) - Timestamp when task was last updated

### Next Steps

Once the table is created, we'll proceed to create Lambda functions that will interact with this table.
