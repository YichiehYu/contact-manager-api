# Contact Manager API

A Spring Boot backend portfolio project for Java Backend Engineer applications.

## Tech Stack

- Java 17
- Spring Boot 3
- Spring Security
- JWT Authentication
- Redis Token Blacklist
- MySQL
- Spring Data JPA / Hibernate
- Docker Compose
- Swagger / OpenAPI

## Features

- User registration and login
- JWT access token authentication
- Refresh token mechanism
- Logout with Redis token blacklist and TTL
- Contact CRUD API
- Pagination, sorting and keyword search
- MySQL table indexes
- Controller / Service / Repository layered architecture
- DTO pattern to avoid exposing Entity directly
- Global exception handling

## API Endpoints

### Auth

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register user |
| POST | `/api/auth/login` | Login and get tokens |
| POST | `/api/auth/refresh` | Get new access token |
| POST | `/api/auth/logout` | Revoke refresh token and blacklist access token |

### Contacts

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/contacts` | List contacts with pagination/search |
| GET | `/api/contacts/{id}` | Get one contact |
| POST | `/api/contacts` | Create contact |
| PUT | `/api/contacts/{id}` | Update contact |
| DELETE | `/api/contacts/{id}` | Delete contact |

## Run with Docker

```bash
docker compose up --build
```

Swagger UI:

```text
http://localhost:8080/swagger-ui.html
```

## Example Request

### Register

```bash
curl -X POST http://localhost:8080/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"123456"}'
```

### Create Contact

```bash
curl -X POST http://localhost:8080/api/contacts \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -d '{"name":"Tom","email":"tom@example.com","phone":"0912345678"}'
```

## Interview Talking Points

- JWT is stateless and suitable for RESTful APIs.
- Redis blacklist solves the logout limitation of JWT.
- TTL allows blacklisted tokens to expire automatically.
- DTO prevents sensitive data exposure and lazy loading serialization problems.
- Indexes improve query performance for frequently searched fields.
- Docker Compose makes the project easier to run with MySQL and Redis.
