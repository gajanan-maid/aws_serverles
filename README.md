# AWS Serverless Project

A comprehensive serverless application built on Amazon Web Services, showcasing modern cloud-native architecture patterns and best practices.

## 📋 Table of Contents

- [Overview](#overview)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Deployment](#deployment)
- [API Documentation](#api-documentation)
- [Architecture](#architecture)
- [Contributing](#contributing)
- [License](#license)

## Overview

This AWS Serverless project demonstrates a scalable, cost-effective solution leveraging AWS services to build modern applications without managing infrastructure. The project combines frontend and backend components to create a fully functional serverless system.

## Technology Stack

### Frontend
- **HTML** (59.7%) - Structure and markup
- **JavaScript** (23.5%) - Interactivity and client-side logic

### Backend
- **Python** (16.8%) - Serverless functions and business logic

### AWS Services
- **AWS Lambda** - Serverless compute
- **Amazon API Gateway** - RESTful API management
- **Amazon DynamoDB** - NoSQL database
- **Amazon S3** - Static content and file storage
- **AWS CloudFormation** - Infrastructure as Code (IaC)
- **AWS CloudWatch** - Monitoring and logging

## Project Structure

```
aws_serverles/
├── frontend/
│   ├── index.html
│   ├── css/
│   ├── js/
│   └── assets/
├── backend/
│   ├── functions/
│   │   ├── handler.py
│   │   └── [lambda_functions]
│   └── requirements.txt
├── infrastructure/
│   ├── template.yaml
│   └── config/
├── tests/
│   ├── unit/
│   └── integration/
└── README.md
```

## Features

- ✨ **Serverless Architecture** - No server management required
- 🚀 **Scalability** - Auto-scales with demand
- 💰 **Cost-Effective** - Pay only for what you use
- 🔒 **Secure** - Built-in AWS security features
- 📱 **Responsive Frontend** - Modern HTML/JavaScript interface
- ⚡ **Real-time Processing** - Lambda-powered backend
- 📊 **Data Persistence** - DynamoDB integration
- 🌐 **API-Driven** - RESTful API endpoints

## Prerequisites

Before you begin, ensure you have the following installed:

- [AWS CLI](https://aws.amazon.com/cli/) - Command line interface for AWS
- [Python 3.9+](https://www.python.org/downloads/) - For Lambda functions
- [Node.js](https://nodejs.org/) - Optional, for build tools
- [Git](https://git-scm.com/) - Version control
- AWS Account with appropriate permissions

### Configuration

Set up AWS credentials:

```bash
aws configure
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/gajanan-maid/aws_serverles.git
cd aws_serverles
```

### 2. Install Dependencies

#### Backend (Python)

```bash
cd backend
pip install -r requirements.txt
```

#### Frontend (JavaScript)

```bash
cd frontend
npm install  # If using npm for build tools
```

### 3. Local Testing

#### Test Lambda Functions Locally

```bash
sam local start-api
```

#### Run Unit Tests

```bash
pytest tests/unit/
```

## Deployment

### Deploy Using AWS SAM

1. Build the project:

```bash
sam build
```

2. Deploy to AWS:

```bash
sam deploy --guided
```

3. Follow the prompts to configure:
   - Stack name
   - AWS Region
   - S3 bucket for artifacts
   - CloudFormation capabilities

### Deploy Frontend to S3

```bash
aws s3 sync frontend/ s3://your-bucket-name/
```

### Enable CloudFront (Optional)

Create a CloudFront distribution pointing to your S3 bucket for optimized content delivery.

## API Documentation

### Base URL

```
https://api.example.com/
```

### Example Endpoints

#### GET /items

Retrieve all items from the database.

**Response:**
```json
{
  "items": [
    {
      "id": "1",
      "name": "Item Name",
      "created_at": "2026-06-08T10:00:00Z"
    }
  ]
}
```

#### POST /items

Create a new item.

**Request:**
```json
{
  "name": "New Item"
}
```

**Response:**
```json
{
  "id": "123",
  "name": "New Item",
  "created_at": "2026-06-08T10:00:00Z"
}
```

#### GET /items/{id}

Retrieve a specific item by ID.

**Response:**
```json
{
  "id": "123",
  "name": "Item Name",
  "created_at": "2026-06-08T10:00:00Z"
}
```

#### DELETE /items/{id}

Delete an item by ID.

**Response:**
```json
{
  "message": "Item deleted successfully"
}
```

## Architecture

### High-Level Architecture Diagram

```
┌─────────────────────────────────────────────────────────┐
│                      End User                            │
└────────────────┬────────────────────────────────────────┘
                 │
┌────────────────▼────────────────────────────────────────┐
│         CloudFront / S3 (Frontend)                       │
│         HTML, CSS, JavaScript                            │
└────────────────┬────────────────────────────────────────┘
                 │
┌────────────────▼────────────────────────────────────────┐
│         API Gateway                                      │
│         RESTful Endpoints                                │
└────────────────┬────────────────────────────────────────┘
                 │
┌────────────────▼────────────────────────────────────────┐
│         AWS Lambda                                       │
│         Python Functions                                │
└────────────────┬────────────────────────────────────────┘
                 │
         ┌───────┴────────┐
         │                │
┌────────▼──────┐  ┌──────▼──────────┐
│   DynamoDB    │  │   CloudWatch    │
│   (Database)  │  │   (Logging)     │
└───────────────┘  └─────────────────┘
```

### Key Components

1. **Frontend Layer** - Static assets hosted on S3 with CloudFront CDN
2. **API Layer** - API Gateway for request routing
3. **Compute Layer** - Lambda functions for business logic
4. **Data Layer** - DynamoDB for persistent storage
5. **Monitoring** - CloudWatch for logs and metrics

## Monitoring & Logging

View Lambda function logs:

```bash
aws logs tail /aws/lambda/your-function-name --follow
```

Monitor with CloudWatch Dashboard:

```bash
aws cloudwatch get-dashboard --dashboard-name YourDashboard
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Troubleshooting

### Common Issues

**Issue: Lambda timeout errors**
- Increase Lambda timeout in CloudFormation template
- Optimize function code for performance

**Issue: API Gateway 403 Forbidden**
- Check IAM permissions for Lambda execution role
- Verify CORS configuration

**Issue: DynamoDB throttling**
- Enable auto-scaling for DynamoDB tables
- Review partition key design

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For issues, questions, or suggestions, please open an issue on GitHub.

---

**Last Updated:** June 8, 2026

**Project Repository:** [gajanan-maid/aws_serverles](https://github.com/gajanan-maid/aws_serverles)
