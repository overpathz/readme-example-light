# Java Web Application with REST API

## Overview
This Java-based web application provides a RESTful API with a focus on security and performance. It features user authentication and authorization using JWT tokens, access control based on user roles, and a relational database for persistent data storage. The application is designed with a clean architecture, separating concerns into repository, service, and controller layers, alongside utility classes for common functions.

## Features
- **REST API**: Exposes endpoints for managing resources, including CRUD operations.
- **Authentication and Authorization**: Implements JWT-based authentication and role-based access control to endpoints.
- **Relational Database Integration**: Utilizes a relational database to store and manage application data.
- **Comprehensive Test Coverage**: Includes unit and integration tests to ensure functionality and reliability.
- **Logging**: Incorporates logging for monitoring and debugging purposes.
- **Project Structure**:
  - `repository`: Data access layer for interacting with the database.
  - `service`: Contains business logic and data processing.
  - `util`: Utility classes and common functions.
  - `controller`: REST controllers to handle API requests.

## API Endpoints

Below is a list of available API endpoints with their respective HTTP methods, descriptions, required roles, and parameters.

| Endpoint                     | Method | Description                             | Required Role | Parameters/Body                                    |
|------------------------------|--------|-----------------------------------------|---------------|----------------------------------------------------|
| `/api/authenticate`          | POST   | Authenticates user and returns JWT      | None          | `username`, `password`                             |
| `/api/users`                 | GET    | Retrieves all users                     | Admin         | None                                               |
| `/api/users/{id}`            | GET    | Retrieves a user by ID                  | Admin/User    | `id`: User ID                                      |
| `/api/users`                 | POST   | Creates a new user                      | Admin         | User JSON object                                   |
| `/api/users/{id}`            | PUT    | Updates an existing user                | Admin/User    | `id`: User ID, User JSON object                    |
| `/api/users/{id}`            | DELETE | Deletes a user                          | Admin         | `id`: User ID                                      |
| `/api/protected/resource`    | GET    | Accesses a protected resource           | User          | None                                               |

### Parameters and Body Details
*need to use Swagger for this*

## Getting Started

### Prerequisites
- JDK 11 or later
- Maven
- A relational database (e.g., MySQL, PostgreSQL)

### Setup
1. Clone the repository to your local machine.
2. Configure the database connection in `src/main/resources/application.properties`.
3. Run the database migration scripts located in `src/main/resources/db/migration` to set up your database schema.
4. Build the project using Maven: `mvn clean install`.
5. Run the application: `java -jar target/your-application.jar`.

## Usage
After starting the application, you can interact with the API using tools like Postman or Curl. Below are some example requests:

### Authenticate
```bash
curl -X POST http://localhost:8080/api/authenticate -d "username=user&password=password"
