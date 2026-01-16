# Serverless-Event-Driven-Employee-Onboarding-Offboarding-System-on-AWS

# 📘 Project Overview

This project is a serverless, event-driven cloud application designed to manage the employee lifecycle, specifically onboarding and offboarding, using AWS managed services.

The system exposes secure REST APIs for employee operations, stores data in a scalable NoSQL database, sends real-time and scheduled email notifications, and follows cloud security best practices without managing any servers.

# 🧩 Architecture Type

Serverless Architecture

Event-Driven System

REST API–Based Backend

Microservices-oriented Design

Cloud-Native Application

# Architecture Diagram
<img width="1334" height="625" alt="arc" src="https://github.com/user-attachments/assets/20245ec4-177f-477c-a881-ebcc3b61c5fd" />


# 🛠️ AWS Services Used

AWS Lambda – Business logic execution

Amazon API Gateway – REST API exposure

Amazon DynamoDB – Employee data storage

Amazon SNS – Email notifications

Amazon EventBridge – Scheduled automation (every 4 hours)

AWS Secrets Manager – Secure authentication token storage

Amazon CloudWatch – Logging and monitoring

IAM Roles & Policies – Secure service permissions

# 📂 System Components
# 1️⃣ API Gateway

Exposes REST endpoints for employee operations

Routes requests to Lambda functions

Resources & Methods

# /employee

POST → Create employee (Onboarding)

PATCH → Update employee password

# /employeer

GET → Fetch employee(s)

DELETE → Delete employee (Offboarding)

# 2️⃣ Lambda Functions
# EmployeeCrudService

Handles all CRUD operations

Interacts with DynamoDB

Validates authorization using Secrets Manager

Triggers onboarding or offboarding Lambdas

# OnboardLambda

Triggered on POST and PATCH

Sends onboarding-related SNS notifications

Runs scheduled batch jobs every 4 hours

# OffboardLambda

Triggered on GET and DELETE

Sends offboarding-related SNS notifications

Runs scheduled batch jobs every 4 hours

# 3️⃣ DynamoDB

Stores employee records with attributes:

employeeid

name

email

password

orgEmail

createdAt

# 4️⃣ Security (Secrets Manager)

Stores authentication token securely

Prevents hardcoding sensitive credentials

Lambda retrieves secrets at runtime

# 5️⃣ Notifications (SNS)

Email alerts are sent for:

Employee creation

Password updates

Data deletion

Scheduled batch summaries

# 6️⃣ Automation (EventBridge)

Triggers onboarding & offboarding Lambdas every 4 hours

Sends batch summary notifications

# 🔄 CRUD Operations Mapping
  | Process     | HTTP Method | Operation        |
  
  | ----------- | ----------- | ---------------- |
  
  | Onboarding  | POST        | Create employee  |
  
  | Onboarding  | PATCH       | Update password  |
  
  | Offboarding | GET         | Read employee(s) |
  
  | Offboarding | DELETE      | Delete employee  |

# 🔐 Authentication Flow

Client sends request with token in header

Lambda retrieves secret from Secrets Manager

Token is validated

Request is processed only if authorized

# 🧪 Testing

APIs are tested using Postman

Authorization token is passed as a request header

Supports all CRUD operations

# 📊 Monitoring & Logging

All Lambda executions are logged in CloudWatch

Errors and execution details are available for debugging

Metrics can be monitored for performance

# ⚙️ How to Deploy (High-Level Steps)

Create DynamoDB table

Create SNS topic and subscribe email

Store authentication token in Secrets Manager

Create IAM roles with least privilege

Deploy Lambda functions

Configure API Gateway resources & methods

Enable Lambda proxy integration

Deploy API Gateway stages

Create EventBridge scheduled rules

Test APIs using Postman

# ✅ Key Features

Fully serverless (no server management)

Secure API authentication

Scalable NoSQL data storage

Real-time and scheduled notifications

Modular Lambda design

Event-driven automation

Cost-efficient and cloud-native

# 📌 Project Use Cases

HR onboarding automation

Secure employee data management

Automated operational notifications

Cloud operations workflow simulation

# 🧠 Technical Highlights

RESTful API design

Event-driven architecture

Secure secrets handling

Asynchronous messaging

Scheduled batch processing

Microservices-oriented Lambda design
