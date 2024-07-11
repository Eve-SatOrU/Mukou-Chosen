# **Mukou Chōsen** (無効挑戦)

Welcome to **Mukou Chōsen** (無効挑戦) - a fun and secure voting system where users can register, vote for candidates, and view results. This system includes authentication, admin controls, and ensures that users can only vote once , ensure security staff.

## Features

- **User Registration and Authentication**
- **Admin Controls to Add Candidates**
- **Secure Voting System**
- **Prevention of Duplicate Voting**
- **Error Handling and Logging**
- **API Documentation with Swagger**

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Project Structure](#project-structure)
- [Extra Features](#extra-features)
- [Contributing](#contributing)

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Eve-SatOrU/mukou-chosen.git
   cd mukou-chosen
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment variables:**
   Create a `.env` file in the root directory and add the following:
   ```
   DATABASE_URL=mysql://user:password@localhost:5432/mydb
   JWT_SECRET=your_jwt_secret
   ```

4. **Set up the database:**
   ```bash
   npx prisma migrate dev --name init
   npx prisma generate
   ```
5. **studio:**
   ```bash
   npx prisma studio
   ```

6. **Start the server:**
   ```bash
   npm start
   ```

## Usage

### Register a New User
```http
POST /users/register
Content-Type: application/json

{
  "username": "yourusername",
  "password": "yourpassword",
  "role": "user" // or "admin"
}
```

### Login
```http
POST /users/login
Content-Type: application/json

{
  "username": "yourusername",
  "password": "yourpassword"
}
```

### Add a Candidate (Admin only)
```http
POST /candidates/add
Content-Type: application/json
Authorization: Bearer <your_jwt_token>

{
  "name": "Candidate Name"
}
```

### Vote for a Candidate
```http
POST /votes
Content-Type: application/json
Authorization: Bearer <your_jwt_token>

{
  "candidateId": "some-string-id"
}
```

## API Documentation

API documentation is available via Swagger. After starting the server, visit:
```
http://localhost:3000/api-docs
```

## Project Structure

```
Mukou-Chosen/
├── prisma/
│   ├── migrations/
│   └── schema.prisma
├── routes/
│   ├── candidate.js
│   ├── user.js
│   └── vote.js
├── middleware/
│   └── auth.js
├── util/
│   └── logger.js
│   └── swagger.yaml
├── .env
├── app.js
├── package.json
├── swagger.js
└── README.md
```

## Extra Features

- **Authentication System:** Secure login and registration using JWT.
- **Admin Role:** Admins can add new candidates to the voting system.
- **Error Handling:** Custom error pages and logging for server-side errors.
- **Swagger UI:** Easy-to-use API documentation interface.

## Contributing

We welcome contributions! Please fork the repository and create a pull request with your changes.
