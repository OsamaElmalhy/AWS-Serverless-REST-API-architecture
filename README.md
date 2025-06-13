# AWS-Serverless-REST-API-architecture


## 📌 Project Overview

This project demonstrates a fully serverless architecture built on AWS to host a secure, scalable, and cost-effective REST API for managing a simple to-do list or customer records. The backend is implemented using **Amazon API Gateway**, **AWS Lambda**, and **Amazon DynamoDB** to perform CRUD (Create, Read, Update, Delete) operations. The frontend is hosted using **Amazon S3** and delivered via **CloudFront**, while **Amazon Cognito** handles authentication.

---

## 🧱 Architecture Summary

![Architecture Diagram](./96e4330e-a15b-4533-aa97-a54780065f3e.png)

### 🔧 Services and Their Roles

| Service                   | Role                                                                 |
|---------------------------|----------------------------------------------------------------------|
| **Route 53**              | Domain Name System (DNS) that routes client requests to CloudFront. |
| **AWS Certificate Manager** | Issues and manages the SSL/TLS certificates for HTTPS traffic.     |
| **CloudFront**            | CDN to serve the frontend (from S3) and backend (API Gateway) content securely and globally. |
| **S3 Website Bucket**     | Hosts the static frontend files (HTML/CSS/JS).                      |
| **Amazon Cognito**        | Manages user authentication (sign-up, sign-in, token-based auth).    |
| **API Gateway**           | Exposes RESTful endpoints and forwards requests to Lambda functions. |
| **AWS Lambda**            | Serverless compute to handle business logic for CRUD operations.     |
| **IAM Policy**            | Grants secure access for Lambda functions to interact with DynamoDB. |
| **DynamoDB**              | NoSQL database to store and retrieve application data.               |
| **CloudWatch**            | Logs API usage, Lambda executions, and monitors the application.     |

---

## 🌐 How the Architecture Works

1. **Frontend Hosting**
   - A user visits your domain managed by **Route 53**, which routes the request to **CloudFront**.
   - CloudFront fetches and caches frontend content from the **S3 Website Bucket** and serves it securely using an SSL certificate from **AWS Certificate Manager**.

2. **Authentication**
   - When authentication is needed, the frontend communicates with **Amazon Cognito** to handle user registration and login securely.

3. **API Requests**
   - Authenticated users make requests to the REST API.
   - Requests hit **API Gateway**, which acts as the entry point for backend operations.
   - API Gateway forwards these requests to the appropriate **AWS Lambda** function.

4. **Business Logic and Data**
   - Lambda executes logic for handling the request (e.g., add a to-do item or fetch a customer record).
   - Lambda uses an **IAM Policy** to securely interact with **DynamoDB**, where all data is stored.
   - **CloudWatch** logs all API and Lambda activity for monitoring and debugging.

---

## ✅ Features

- Fully **serverless** and scalable
- HTTPS support with **SSL/TLS**
- Secure **authentication** via Amazon Cognito
- Low-latency global delivery using **CloudFront**
- CRUD operations without server management
- Logging and monitoring via **CloudWatch**

---


---

## 🚀 Deployment

You can deploy this architecture using AWS SAM or the Serverless Framework. Be sure to configure your:
- S3 bucket permissions
- API Gateway endpoints
- Cognito user pools and app clients
- Lambda environment variables and IAM roles

---

## 📌 Notes

- Ensure CORS is configured correctly on both API Gateway and S3.
- Fine-tune IAM roles to adhere to the principle of least privilege.
- DynamoDB tables should have proper partition keys and indexes for efficient querying.




