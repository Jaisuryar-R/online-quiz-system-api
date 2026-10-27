# Online Quiz System API

A RESTful backend API for managing quizzes, multiple-choice questions, participants, and quiz submissions using Node.js, Express.js, and MySQL.

## Overview

The Online Quiz System allows participants to register, take quizzes, submit answers, and receive calculated scores. It also provides endpoints for managing quizzes and their questions.

## Features

- Create and retrieve quizzes
- Add multiple-choice questions and answer options
- Register participants
- Hash participant passwords using bcrypt
- Submit quiz answers and calculate scores
- Store quiz results in MySQL
- Validate submissions and option selections
- Return JSON responses through REST API endpoints

## Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Express.js | Backend framework |
| MySQL | Relational database |
| mysql2 | Database connectivity |
| bcryptjs | Password hashing |
| dotenv | Environment configuration |
| PowerShell | API testing |

## Project Structure

```text
Task5-Online-Quiz-System/
├── src/
│   ├── config/
│   │   └── db.js
│   ├── routes/
│   │   ├── quizRoutes.js
│   │   ├── questionRoutes.js
│   │   ├── userRoutes.js
│   │   └── submitRoutes.js
│   └── app.js
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

## Database

**Database name:** `online_quiz_db`

The documented database contains these tables:

- `users` — participant details and password hashes
- `quizzes` — quiz information
- `questions` — questions associated with quizzes
- `options` — multiple-choice options and correct-answer flags
- `results` — participant scores and submission details

## Setup Instructions

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Environment Variables

Create a local `.env` file in the project root:

```env
PORT=5002
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=online_quiz_db
DB_PORT=3306
JWT_SECRET=your_secret_value
```

Replace the example values with your local configuration. Never upload real credentials or secrets to GitHub.

### 3. Start the Server

```bash
node src/app.js
```

The documented configuration uses port `5002`. The actual port depends on the application configuration.

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/quizzes` | Retrieve quizzes |
| GET | `/api/quizzes/:id` | Retrieve a quiz and its questions |
| POST | `/api/quizzes` | Create a quiz |
| POST | `/api/quizzes/:quizId/questions` | Add questions and options |
| POST | `/api/users/register` | Register a participant |
| POST | `/api/quizzes/:quizId/submit` | Submit answers and calculate a score |

## Example Requests

### Create a Quiz

**POST** `/api/quizzes`

```json
{
  "title": "Java Fundamentals",
  "description": "Basic Java programming quiz"
}
```

### Register a Participant

**POST** `/api/users/register`

```json
{
  "name": "Test Participant",
  "email": "participant1@example.com",
  "password": "TestPass123!"
}
```

### Submit Quiz Answers

**POST** `/api/quizzes/1/submit`

```json
{
  "user_id": 1,
  "answers": [
    {
      "question_id": 1,
      "option_id": 1
    }
  ]
}
```

Use valid IDs from your database when testing requests.

## Testing

The supplied project notes report a successful sample quiz submission with a score of `1/1` and a percentage of `100%`.

## Security Considerations

- Store credentials in environment variables.
- Exclude `.env` and `node_modules/` from version control.
- Hash participant passwords before storing them.
- Add and verify authentication and authorization before production use.

## Internship Task

**Program:** CodSoft Backend Development Internship

**Task:** Task 5 — Online Quiz System API

## Conclusion

The Online Quiz System API documents backend functionality for quiz management, participant registration, question handling, answer submission, and score calculation using Node.js, Express.js, and MySQL.
