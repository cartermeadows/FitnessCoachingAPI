# Fitness Coaching API - ITIS 4166-052

A fitness platform used by coaches to create and assign workout plans to clients who can also track their progress and record a diary.
# Fitness Coaching API

A RESTful backend API for a fitness coaching platform that allows coaches to create training programs for clients, track workout performance, and manage client training diaries. This project was built with Node.js, Express, PostgreSQL, Prisma, JWT authentication, and Swagger/OpenAPI documentation.

## Live Demo

**Swagger Documentation:** `https://itis-4166-052-fitnesscoachingapi.onrender.com/api-docs/`

## Features

* User signup and login with JWT authentication
* Role-based access control for coaches and clients
* Coaches can create, view, update, and delete training programs
* Clients can view assigned programs
* Workout logs for tracking sets, reps, load, RPE, and notes
* Client diary entries for mood, energy level, soreness, and comments
* PostgreSQL database managed with Prisma ORM
* OpenAPI/Swagger documentation for testing endpoints
* Input validation and error handling for invalid requests
* Deployed using Render

## Tech Stack

* **Backend:** Node.js, Express.js
* **Database:** PostgreSQL
* **ORM:** Prisma
* **Authentication:** JWT
* **Documentation:** Swagger UI / OpenAPI 3.1
* **Testing & Tools:** Postman, Jest, Git
* **Deployment:** Render

## Main Resources

### Users

Users can sign up and log in. Each user has a role of either `coach` or `client`.

### Programs

Training programs are created by coaches and assigned to clients. Programs include a title, goal, duration in weeks, and status.

### Workout Logs

Workout logs allow clients to record workout performance, including prescribed sets/reps, actual sets/reps, load, RPE, and notes.

### Diaries

Diary entries allow clients to track subjective training feedback such as mood, energy level, soreness level, and comments.

## API Endpoints

### Authentication

| Method | Endpoint           | Description                  |
| ------ | ------------------ | ---------------------------- |
| POST   | `/api/auth/signup` | Register a new user          |
| POST   | `/api/auth/login`  | Log in and receive JWT token |

### Programs

| Method | Endpoint            | Description                                      |
| ------ | ------------------- | ------------------------------------------------ |
| GET    | `/api/programs`     | Get programs available to the authenticated user |
| POST   | `/api/programs`     | Create a new program                             |
| GET    | `/api/programs/:id` | Get a specific program                           |
| PUT    | `/api/programs/:id` | Update a program                                 |
| DELETE | `/api/programs/:id` | Delete a program                                 |

### Workout Logs

| Method | Endpoint                | Description                |
| ------ | ----------------------- | -------------------------- |
| GET    | `/api/workout-logs`     | Get workout logs           |
| POST   | `/api/workout-logs`     | Create a workout log       |
| GET    | `/api/workout-logs/:id` | Get a specific workout log |
| PUT    | `/api/workout-logs/:id` | Update a workout log       |
| DELETE | `/api/workout-logs/:id` | Delete a workout log       |

### Diaries

| Method | Endpoint           | Description                |
| ------ | ------------------ | -------------------------- |
| GET    | `/api/diaries`     | Get diary entries          |
| POST   | `/api/diaries`     | Create a diary entry       |
| GET    | `/api/diaries/:id` | Get a specific diary entry |
| PUT    | `/api/diaries/:id` | Update a diary entry       |
| DELETE | `/api/diaries/:id` | Delete a diary entry       |

## Example Request

### Create a Program

```json
{
  "client_id": 5,
  "title": "Beginner Strength Program",
  "goal": "Build foundational strength",
  "duration_weeks": 8,
  "status": "active"
}
```

### Example Response

```json
{
  "id": 1,
  "coach_id": 1,
  "client_id": 5,
  "title": "Beginner Strength Program",
  "goal": "Build foundational strength",
  "duration_weeks": 8,
  "status": "active",
  "created_at": "2026-04-28T00:00:00.000Z",
  "updated_at": "2026-04-28T00:00:00.000Z"
}
```

## Local Installation

### 1. Clone the repository

```bash
git clone https://github.com/cartermeadows/FitnessCoachingAPI
cd FitnessCoachingAPI
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the root directory.

```env
DATABASE_URL="your_postgresql_connection_string"
JWT_SECRET="your_jwt_secret"
JWT_EXPIRES_IN="1d"
```

### 4. Run Prisma migrations

```bash
npx prisma migrate dev
```

### 5. Seed the database

```bash
npm run seed
```

### 6. Start the server

```bash
npm start
```

The API should now be running locally.

```text
http://localhost:3000
```

## Authentication

Protected routes require a JWT token.

After logging in, include the token in the request header:

```text
Authorization: Bearer your_token_here
```

## Project Highlights

* Designed a normalized relational database schema using PostgreSQL and Prisma
* Implemented full CRUD functionality across multiple related resources
* Added authentication and authorization logic using JWT and user roles
* Built API documentation with Swagger for easy testing and grading
* Deployed the application publicly using Render
* Tested endpoint behavior for valid requests, invalid input, unauthorized access, forbidden actions, and missing resources

## Future Improvements

* Add refresh tokens
* Add password reset functionality
* Add coach-client invitation workflow
* Add advanced filtering and pagination
* Add frontend dashboard for coaches and clients
* Expand automated test coverage

## Author

**Carter Meadows**
Computer Science Graduate — Cyber Security Concentration
University of North Carolina at Charlotte
