# MERN Stack Book Management System — Backend

A REST API backend for a Book Management System built using **Node.js, Express.js, MongoDB, and Mongoose**.

This backend provides user registration, login, JWT-based authentication, protected book management operations, pagination, and search functionality. It is designed to integrate with a React frontend.

## Features

- User registration and login
- JWT-based authentication and authorization
- Password hashing using bcrypt
- Create, read, update, and delete (CRUD) operations for books
- Pagination and search functionality
- Protected API routes using authentication middleware
- MongoDB local and MongoDB Atlas support
- REST API integration with a React frontend

## Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Express.js | Backend framework |
| MongoDB | NoSQL database |
| Mongoose | MongoDB object modeling |
| JWT | Authentication and authorization |
| bcryptjs | Password hashing |
| dotenv | Environment variable management |
| CORS | Cross-origin resource sharing |

## Project Structure

```text
mern_stack_server_app/
│
├── controllers/
│   ├── bookController.js
│   └── authController.js
│
├── routes/
│   ├── bookRoutes.js
│   └── authRoutes.js
│
├── models/
│   ├── Book.js
│   └── User.js
│
├── middleware/
│   └── authMiddleware.js
│
├── seed.js
├── server.js
├── package.json
├── package-lock.json
├── .gitignore
└── README.md
```

*Note: This structure describes the main application files. Individual files may vary depending on the repository version.*

## Architecture

The application follows an MVC-inspired structure.

### Controllers
Handle application logic, process requests, interact with database models, and return API responses.

### Routes
Define API endpoints and connect incoming requests to their corresponding controller functions.

### Models
Define MongoDB document structures and schemas using Mongoose.

### Middleware
Handles JWT verification and protects routes that require an authenticated user.

## Getting Started

### Prerequisites

Make sure you have the following installed:

- Node.js (v16 or later)
- npm
- MongoDB local installation or a MongoDB Atlas account
- Postman (optional, for API testing)

### 1. Clone the Repository

```bash
git clone https://github.com/Ayushman7985-outlook/Mern-Stack-Server-App.git
```

### 2. Navigate to the Project Directory

```bash
cd Mern-Stack-Server-App
```

### 3. Install Dependencies

```bash
npm install
```

### 4. Configure Environment Variables

Create a `.env` file in the project root directory.

For a local MongoDB database:

```env
MONGO_URL=mongodb://localhost:27017/bookdb
PORT=8800
JWT_SECRET=your_secret_key
```

For MongoDB Atlas:

```env
MONGO_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net/bookdb
PORT=8800
JWT_SECRET=your_secret_key
```

Replace the placeholders with your actual database credentials and a secure JWT secret.

**Important:** Never commit your `.env` file or expose database credentials and JWT secrets publicly.

### 5. Seed the Database

If you want to populate the database with the sample records provided by the project, run:

```bash
node seed.js
```

Run this only when you need the initial sample data.

### 6. Start the Server

```bash
node server.js
```

The backend runs on the configured port (8800 by default).

## API Documentation

The following endpoints describe the main authentication and book-management operations.

### Authentication APIs

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Authenticate a user |

**Registration request:**

```json
{
  "username": "example",
  "email": "example@test.com",
  "password": "password123"
}
```

**Login request:**

```json
{
  "email": "example@test.com",
  "password": "password123"
}
```

A successful login returns an authentication token and user information.

### Book Management APIs

| Method | Endpoint | Description |
|---|---|---|
| GET | `/books?page=1&limit=5&search=clean` | Retrieve books with pagination and search |
| POST | `/books` | Create a new book |
| PUT | `/books/:id` | Update an existing book |
| DELETE | `/books/:id` | Delete a book |

**Create book request:**

```json
{
  "title": "Clean Code",
  "author": "Robert C. Martin",
  "year": 2008
}
```

**Authentication:** Protected book-management endpoints require a valid JWT token in the request header.

```http
Authorization: Bearer <JWT_TOKEN>
```

## Application Workflow

```text
React Frontend / Postman
          |
          v
     Express Server
          |
          v
       API Routes
          |
          v
      Controllers
          |
          v
        Models
          |
          v
       MongoDB
          |
          v
     JSON Response
```

## Common Issues

- **MongoDB connection error:** Verify the database URL and connection status.
- **Authentication failure:** Check whether the JWT token is valid and has not expired.
- **Missing environment variables:** Ensure the `.env` file exists and contains the required values.
- **MongoDB Atlas connection issue:** Check whether your IP address is allowed in the Atlas network access settings.
- **API route errors:** Verify the endpoint and route prefix used by the frontend.

## Learning Outcomes

This project demonstrates practical implementation of:

- Backend development using Node.js and Express.js
- REST API design and development
- MongoDB database integration with Mongoose
- JWT authentication and route protection
- Password hashing and authentication workflows
- CRUD operations
- Pagination and search functionality
- Frontend and backend integration

## Live Application

The original project includes a deployed application:

[View Live Application](https://nischalaremanda-mern-crud-app.onrender.com)

## Author & Acknowledgement

**Original Author: Nischal Aremanda**

Backend and Full-Stack Developer

Original backend repository:  
https://github.com/nischalare/mern_stack_server_app

This repository is a personal copy of the original backend project. Credit is retained for the original implementation and project structure.
