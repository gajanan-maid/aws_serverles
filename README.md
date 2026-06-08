# AWS Serverless Project

A simple serverless application built with AWS Lambda, API Gateway, and DynamoDB.

## 📋 Table of Contents

- [Overview](#overview)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Deployment](#deployment)
- [API Endpoints](#api-endpoints)

## Overview

This project demonstrates a scalable serverless architecture using AWS Lambda, API Gateway, and DynamoDB without managing infrastructure.

## Technology Stack

- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Python (Lambda functions)
- **Database:** DynamoDB
- **Storage:** S3
- **API:** API Gateway

## Project Structure

```
aws_serverles/
├── frontend/
│   ├── index.html
│   ├── css/
│   └── js/
├── backend/
│   ├── functions/
│   │   └── handler.py
│   └── requirements.txt
├── tests/
└── README.md
```

## Prerequisites

- AWS CLI configured with credentials
- Python 3.9+
- Git

## Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/gajanan-maid/aws_serverles.git
cd aws_serverles
```

### 2. Install Backend Dependencies

```bash
cd backend
pip install -r requirements.txt
```

## Deployment

### Deploy Backend to AWS

```bash
# Deploy using AWS CLI/Lambda directly
aws lambda create-function --function-name my-function \
  --runtime python3.9 \
  --role arn:aws:iam::ACCOUNT:role/lambda-role \
  --handler backend/functions/handler.lambda_handler \
  --zip-file fileb://function.zip
```

### Deploy Frontend to S3

```bash
aws s3 sync frontend/ s3://your-bucket-name/
```

## API Endpoints

- `GET /items` - Retrieve all items
- `POST /items` - Create new item
- `GET /items/{id}` - Get specific item
- `DELETE /items/{id}` - Delete item

---

**Repository:** [gajanan-maid/aws_serverles](https://github.com/gajanan-maid/aws_serverles)
