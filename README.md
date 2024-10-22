# Nuxt.js Project with PostgreSQL Integration

## Overview
This project is a **Nuxt.js application** that integrates with a **PostgreSQL database**. It demonstrates basic CRUD operations, user authentication, and how to containerize the project using Docker.

## Table of Contents
- [Requirements](#requirements)
- [Setup](#setup)
- [Docker Image Creation](#docker-image-creation)
- [Running the Docker Container](#running-the-docker-container)
- [Interacting with the Application](#interacting-with-the-application)
- [Environment Variables](#environment-variables)
- [Helpful Notes](#helpful-notes)

## Requirements
- **Docker** and **Docker Compose** installed on your system.
- **Node.js** and **npm** (for local development).

## Setup
1. **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd <project-folder>
    ```
2. **Install dependencies:**
    ```bash
    npm install
    ```
3. **Start the development server:**
    ```bash
    npm run dev
    ```

## Docker Image Creation

### Step 1: Build Docker Image
To build a Docker image for the Nuxt.js application:
```bash
docker build -t <image_name>:<tag> .


Running the Docker Container

Step 1: Start the PostgreSQL Container
If not already running, start a PostgreSQL container:
docker run -d --name postgres_container \
  -e POSTGRES_USER=myuser \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -e POSTGRES_DB=mydatabase \
  -p 5432:5432 \
  postgres

Step 2: Start the Nuxt.js Container
To start the Nuxt.js container:
docker run -d --name nuxt_app_container \
  -p 3000:3000 \
  --link postgres_container:postgres \
  -e DB_HOST=postgres \
  -e DB_USER=myuser \
  -e DB_PASSWORD=mysecretpassword \
  -e DB_NAME=mydatabase \
  <image_name>:<tag>

Step 3: Access the Application
Once the containers are running, you can access the application at:
http://localhost:3000
Interacting with the Application
Endpoints
GET /api/users: Retrieve all users.
GET /api/users?id=<user_id>: Retrieve a single user by ID.
POST /api/users: Create a new user. Requires name, email, and password.
PUT /api/users?id=<user_id>: Update an existing user by ID.
DELETE /api/users?id=<user_id>: Delete a user by ID.
POST /api/auth/login: User login.
POST /api/auth/register: User registration.

<img width="885" alt="Screenshot 2024-10-22 at 2 59 48 PM" src="https://github.com/user-attachments/assets/29782914-e168-4aad-b4d6-93672f8fffe4">
<img width="885" alt="Screenshot 2024-10-22 at 2 59 41 PM" src="https://github.com/user-attachments/assets/27e6d646-d13c-422d-a00b-074e65bff454">
<img width="885" alt="Screenshot 2024-10-22 at 2 59 33 PM" src="https://github.com/user-attachments/assets/056b80ef-083c-42f9-8f03-00f1daa3120b">
<img width="885" alt="Screenshot 2024-10-22 at 2 59 05 PM" src="https://github.com/user-attachments/assets/fb75f943-f69f-40e8-a354-7b9606f2006b">
<img width="885" alt="Screenshot 2024-10-22 at 2 59 00 PM" src="https://github.com/user-attachments/assets/1a1e8544-1963-421f-96e7-6b2fb783e02a">
<img width="885" alt="Screenshot 2024-10-22 at 2 58 53 PM" src="https://github.com/user-attachments/assets/1be17b4f-39cd-4c69-9942-4af9f393941d">


