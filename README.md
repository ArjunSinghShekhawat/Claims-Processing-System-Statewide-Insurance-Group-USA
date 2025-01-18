# Claims Processing System

A centralized platform designed to manage and process insurance claims efficiently for the **Statewide Insurance Group**. This system consolidates data from various internal and external sources to streamline the claims handling process.

---

## Table of Contents
1. [Introduction](#introduction)
2. [Project Architecture](#project-architecture)
3. [Project Flow](#project-flow)
4. [Key Features](#key-features)
5. [Technology Stack](#technology-stack)
6. [Database Schema](#database-schema)
7. [REST APIs](#rest-apis)
8. [Use of Tools](#use-of-tools)
   - [Kafka](#use-of-kafka)
   - [Log4j2](#use-log4j2)
   - [Redis Cache](#use-of-redis-cache)

---

## Introduction
The **Claims Processing System** is built to provide:
- Real-time updates on claim status.
- Automated claim evaluation through preset rules.
- Detailed reporting for insurance agents and clients.

The backend is based on a **monolithic architecture** to ensure ease of deployment, scalability, and maintenance.

---

## Project Architecture

### Monolithic Backend
Key components include:
- **Claims Processing Module**: Manages validation, processing, and status updates of insurance claims.
- **User Management Module**: Handles authentication, user account management, and role-based access control.
- **Reporting Module**: Generates detailed reports and analytics.

### Database
- **MySQL**: Used for robust data management and handling complex insurance queries.

### Cache Mechanism
- **Redis**: In-memory cache solution for frequently accessed data (e.g., claim statuses, user profiles).

### Logging Tools
- **Log4j2**: For application logging.
- **Splunk**: For real-time log analysis and visualization.

### Security
- **OAuth**: Implemented for secure access control.

### Messaging System
- **Kafka**: Manages real-time notifications and updates for claims.

---

## Project Flow

### Step 1: Claim Submission and Authentication
1. Insurance agent logs in and submits a new claim.
2. Authentication and authorization are handled via OAuth.
3. Access tokens are generated for secure session management.

### Step 2: Claim Validation and Processing
1. Claims are validated against predefined rules.
2. Valid claims proceed for settlement calculations.

### Step 3: Reporting and Feedback
1. Reports are generated, detailing claim decisions and settlements.
2. Reports are accessible to agents and shared with clients via email.

### Common Activities
- All data transactions and user actions are logged via Splunk.
- Kafka manages real-time data updates.

---

## Key Features
- **Claims Management**: Submission, processing, and tracking.
- **User Authentication**: Role-based access control.
- **Real-time Updates**: Instant claim status notifications using Kafka.
- **Detailed Reporting**: Insights into claims and settlements.

---

## Technology Stack
- **Backend**: Spring Boot (Monolithic Architecture)
- **Database**: MySQL
- **Cache**: Redis
- **Messaging**: Kafka
- **Logging**: Log4j2, Splunk
- **Version Control**: GitLab

---

## Database Schema

### Claims Table
| Field         | Type        | Description                      |
|---------------|-------------|----------------------------------|
| `claim_id`    | Primary Key | Unique identifier for claims     |
| `user_id`     | Foreign Key | References the Users table       |
| `claim_date`  | Date        | Date of claim submission         |
| `claim_amount`| Decimal     | Amount of the claim              |
| `claim_status`| String      | Status (submitted, processed, etc.) |

### Users Table
| Field         | Type        | Description                      |
|---------------|-------------|----------------------------------|
| `user_id`     | Primary Key | Unique identifier for users      |
| `username`    | String      | Login name                      |
| `email`       | String      | Email of the user               |
| `role`        | String      | Role (agent, admin, etc.)        |

... (Other tables follow a similar format)

---

## REST APIs

### Claims Management
- `POST /claims`: Submit a new insurance claim.
- `GET /claims/{claimId}`: Retrieve details of a specific claim.
- `PUT /claims/{claimId}`: Update a claim.
- `DELETE /claims/{claimId}`: Delete a claim.

### User Management
- `POST /users/register`: Register a new user.
- `POST /users/login`: Authenticate a user.
- `GET /users/{userId}`: Retrieve user details.

---

## Use of Tools

### Use of Kafka
- Handles real-time notifications and updates for claims.
- Segregates messages into topics for better organization.

### Use Log4j2
- Replaced default Spring Boot logging with Log4j2.
- Configured YAML for dynamic and structured logging.

### Use of Redis Cache
- Stores frequently accessed claim statuses and reports.
- Enhances system efficiency and reduces database load.


