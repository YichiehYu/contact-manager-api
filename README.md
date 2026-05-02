# Contact Manager API

本專案為使用 Spring Boot 開發的後端作品，展示使用者驗證、Token 管理與 RESTful API 設計能力，並整合 Redis 與 Docker 進行實務部署。

---

## 🚀 技術架構

- Java 17
- Spring Boot 3
- Spring Security
- JWT 驗證機制
- Redis（Token 黑名單）
- MySQL
- Spring Data JPA / Hibernate
- Docker Compose
- Swagger / OpenAPI

---

## ⭐ 專案亮點

- 實作 JWT + Refresh Token 驗證流程
- 使用 Redis Token 黑名單解決 JWT 無法登出問題
- 使用 TTL 自動清除過期 Token
- RESTful API 設計（CRUD + 分頁 + 搜尋）
- 分層架構（Controller / Service / Repository）
- Docker Compose 一鍵啟動環境

---

## 🔐 核心功能

### 使用者驗證
- 註冊 / 登入
- JWT Access Token
- Refresh Token 延長登入狀態

### Token 管理
- Redis 黑名單
- 登出機制（Token 失效）
- TTL 自動過期

### 聯絡人管理
- 新增 / 查詢 / 修改 / 刪除
- 分頁與排序
- 關鍵字搜尋

---

## 🗄️ 資料庫設計

- 使用 MySQL
- 常用查詢欄位建立 Index 提升效能
- 使用 JPA 操作資料

---

## 🧱 系統架構

- Controller：處理 API 請求
- Service：商業邏輯
- Repository：資料庫存取

透過分層設計提升可維護性與擴展性。

---

## 🐳 執行方式

```bash
docker compose up --build
```

Swagger 文件：

http://localhost:8080/swagger-ui.html

---

## 💬 面試重點

- JWT 為無狀態驗證，適合前後端分離架構
- Redis 用於 Token 黑名單，具備高效能與 TTL 支援
- TTL 可自動清除過期 Token
- DTO 可避免敏感資料外洩與 Lazy Loading 問題
- Index 提升查詢效能
- Docker Compose 簡化環境建置

---


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
