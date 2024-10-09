
# User Management API

This project is a simple **RESTful API** built with **Laravel** and **SQLite**, providing endpoints for managing users. It allows for creating, reading, updating, and deleting users, while utilizing Laravel's built-in functionality for validation, error handling, and database migrations.

## Table of Contents

1. [Features](#features)
2. [Requirements](#requirements)
3. [Installation](#installation)
4. [API Endpoints](#api-endpoints)
5. [Testing the API with cURL](#testing-the-api-with-curl)

## Features

- **User management**: CRUD (Create, Read, Update, Delete) functionality for users.
- **Input validation**: Validates data before it is saved or updated.
- **Error handling**: Handles and logs errors in a structured manner.
- **Database migration**: Auto-generates database schema with Laravel migrations.
- **API Documentation**: Integrated Swagger UI for API documentation and testing.
- **SQLite**: In-memory or file-based database for lightweight and simple setup.

## Requirements

- PHP 8.x or higher
- Composer
- Laravel 10.x or higher
- SQLite or any other supported database (PostgreSQL, MySQL, etc.)
- cURL (for testing API endpoints)

## Installation

Follow the steps below to get the project running:

### Step 1: Clone the repository

```bash
git clone https://github.com/yourusername/user-management-api.git
cd user-management-api
```

### Step 2: Install dependencies

Run the following command to install Laravel dependencies:

```bash
composer install
```

### Step 3: Set up the `.env` file

Copy the example environment file and update the necessary variables:

```bash
cp .env.example .env
```

Make sure to configure the database settings in `.env` to use **SQLite**:

```env
DB_CONNECTION=sqlite
DB_DATABASE=/absolute/path/to/database/database.sqlite
```

Create the SQLite database file:

```bash
touch database/database.sqlite
```

### Step 4: Generate the application key

```bash
php artisan key:generate
```

### Step 5: Run migrations

To create the necessary tables in the database, run:

```bash
php artisan migrate
```

### Step 6: Serve the application

You can run the application locally using Laravel’s development server:

```bash
php artisan serve
```

The application will now be running at `http://127.0.0.1:8000`.

## API Endpoints

Here are the main API endpoints for managing users:

### **POST** `/api/users`

Create a new user.

- Request Body (JSON):

  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "password": "secret",
    "role": "user"
  }
  ```

- Response:
  - `201 Created`: User created successfully.

### **GET** `/api/users`

Retrieve a list of all users.

- Response:
  - `200 OK`: List of users.

### **GET** `/api/users/{id}`

Retrieve a specific user by ID.

- Response:
  - `200 OK`: User found.
  - `404 Not Found`: User not found.

### **PUT** `/api/users/{id}`

Update a specific user by ID.

- Request Body (JSON):

  ```json
  {
    "name": "John Updated",
    "email": "john.updated@example.com",
    "password": "newpassword",
    "role": "admin"
  }
  ```

- Response:
  - `200 OK`: User updated successfully.
  - `404 Not Found`: User not found.

### **DELETE** `/api/users/{id}`

Delete a specific user by ID.

- Response:
  - `204 No Content`: User deleted successfully.
  - `404 Not Found`: User not found.

## Testing the API with cURL

You can test the API endpoints using cURL:

### Create a User (POST)

```bash
curl -X POST http://127.0.0.1:8000/api/users \
-H "Content-Type: application/json" \
-d '{"name": "John Doe", "email": "john@example.com", "password": "secret", "role": "user"}'
```

### Get All Users (GET)

```bash
curl -X GET http://127.0.0.1:8000/api/users
```

### Get a Specific User by ID (GET)

```bash
curl -X GET http://127.0.0.1:8000/api/users/1
```

### Update a User (PUT)

```bash
curl -X PUT http://127.0.0.1:8000/api/users/1 \
-H "Content-Type: application/json" \
-d '{"name": "John Updated", "email": "john.updated@example.com", "password": "newpassword", "role": "admin"}'
```

### Delete a User (DELETE)

```bash
curl -X DELETE http://127.0.0.1:8000/api/users/1
```
