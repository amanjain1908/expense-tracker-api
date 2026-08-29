Expense Tracker API (with Docker support)

A RESTful Spring Boot API for tracking personal expenses, categories, and transactions, secured with JWT authentication.

This project is forked from arsan13/expense-tracker-api, which I used as a learning reference for building a Spring Boot + JWT authentication backend. I extended it with Docker support to containerize the application and its database for consistent, one-command local setup.

What I added
Dockerfile — multi-stage build to containerize the Spring Boot application
docker-compose.yml — orchestrates the app and a MySQL container together, networked internally
Environment-based configuration — moved database credentials out of hardcoded config files into environment variables (.env) to avoid committing secrets
Debugged and resolved container networking and database connectivity issues between the app and MySQL containers
Tech Stack
Java 17
Spring Boot, Spring Data JPA
MySQL 8.0
JWT Authentication
Docker & Docker Compose
Maven
Getting Started
Prerequisites
Docker Desktop installed and running
Setup
Clone this repository git clone https://github.com/amanjain1908/expense-tracker-api.git
cd expense-tracker-api
Create a .env file in the project root: DB_PASSWORD=your_mysql_password
(Optional, for running outside Docker) Copy the local properties template and fill in your own credentials: cp src/main/resources/application-local.properties.example src/main/resources/application-local.properties
Build and run everything with Docker Compose: docker compose up --build

The API will be available at http://localhost:7077.

API Endpoints
Method	Endpoint	Description
POST	/api/users/register/	Register a new user
POST	/api/users/login/	Login and receive a JWT
GET	/api/categories/	Get all categories
POST	/api/categories/	Create a new category
GET	/api/categories/{id}	Get a category by ID
PUT	/api/categories/{id}	Update a category
DELETE	/api/categories/{id}	Delete a category
GET	/api/categories/{cid}/transactions/	Get all transactions in a category
POST	/api/categories/{cid}/transactions/	Create a transaction in a category
GET	/api/categories/{cid}/transactions/{tid}	Get a specific transaction
PUT	/api/categories/{cid}/transactions/{tid}	Update a transaction
DELETE	/api/categories/{cid}/transactions/{tid}	Delete a transaction

All endpoints except register/login require a Bearer <token> in the Authorization header.

Notes

This project was built as a hands-on way to strengthen my Spring Boot and Docker skills, using a reference implementation as a starting point and extending it with containerization and secure configuration handling.