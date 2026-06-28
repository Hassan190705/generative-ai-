# Interview AI Assistant

A full-stack interview preparation platform that combines a React frontend with an Express/MongoDB backend and Google Gemini AI.

## Overview

This project helps candidates prepare for job interviews by generating:
- AI-powered interview reports
- Behavioral and technical questions with answering guidance
- Skill gap analysis and day-by-day preparation plans
- Resume PDFs tailored to a target job description

It includes:
- User authentication (register, login, logout)
- JWT-based session handling with cookie storage and token blacklist
- Resume upload for interview report generation
- Google Gemini AI integration via `@google/genai`
- React + Vite frontend with protected routes

## Repository Structure

- `Backend/` - Express API server
  - `server.js` - application entry point
  - `src/app.js` - Express app configuration
  - `src/config/database.js` - MongoDB connection
  - `src/controllers/` - request handlers
  - `src/middlewares/` - auth and file upload middleware
  - `src/models/` - MongoDB schemas
  - `src/routes/` - API endpoints
  - `src/services/ai.service.js` - AI report and resume generation logic

- `Frontend/` - React application
  - `src/App.jsx` - app root with providers
  - `src/app.routes.jsx` - route definitions
  - `src/features/` - auth and interview features
  - `src/style/` - global styles

## Features

- Register and login with email/password
- Generate interview reports using resume text, self-description, and job description
- Persist interview reports to MongoDB
- Download generated resume PDFs
- Protected frontend routes for authenticated users
- CORS configured to allow frontend access from `http://localhost:5173`

## Environment Variables

Create a `.env` file inside `Backend/` with the following values:

```
MONGO_URI=your-mongodb-connection-string
JWT_SECRET=your-jwt-secret
GOOGLE_GENAI_API_KEY=your-google-genai-api-key
```

## Setup

### Backend

1. Open a terminal in `Backend/`
2. Install dependencies:
   `npm install`
3. Start the server:
   `npm run dev`

The backend listens on `http://localhost:3000`.

### Frontend

1. Open a terminal in `Frontend/`
2. Install dependencies:
   `npm install`
3. Start the frontend:
   `npm run dev`

The frontend runs on `http://localhost:5173`.

## API Endpoints

### Auth
- `POST /api/auth/register` - register a new user
- `POST /api/auth/login` - authenticate and set cookie token
- `GET /api/auth/logout` - logout and blacklist current token
- `GET /api/auth/get-me` - get current user profile

### Interview
- `POST /api/interview/` - generate interview report (`multipart/form-data`, field `resume`)
- `GET /api/interview/` - list all user interview reports
- `GET /api/interview/report/:interviewId` - fetch a specific report
- `POST /api/interview/resume/pdf/:interviewReportId` - generate a resume PDF for a report

## Notes

- The backend expects the frontend origin at `http://localhost:5173`
- Resume report generation uses `Google Gemini` through the `@google/genai` package
- PDF creation depends on `puppeteer`

## Recommended Stack

- Node.js
- Express
- MongoDB
- React
- Vite
- Google Gemini AI

## License

This project does not include a license file. Add one if you plan to open source it.
