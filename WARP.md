# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a simple Node.js REST API for an Address Book application built with Express.js and MongoDB. It provides basic CRUD operations for managing addresses with title and description fields.

## Architecture

The application follows a standard MVC pattern:

- **Models** (`models/`): Mongoose schemas defining data structure
- **Controllers** (`controllers/`): Business logic for handling requests
- **Routes** (`routes/`): API endpoint definitions
- **Configuration** (`config/`): Database connection setup

### Key Components

- **Entry Point**: `index.js` - Express server setup with CORS and middleware configuration
- **Database**: MongoDB via Mongoose ODM with connection configured in `config/db.js`
- **API Endpoints**: All routes are prefixed with `/api/addresses`
  - GET `/api/addresses` - Retrieve all addresses
  - POST `/api/addresses` - Create new address
  - PUT `/api/addresses/:id` - Update existing address
  - DELETE `/api/addresses/:id` - Delete address

## Development Commands

### Setup and Installation

```bash
npm install
```

### Environment Configuration

```bash
cp .env.sample .env
# Edit .env with your MongoDB connection string
```

### Running the Application

```bash
npm start                    # Production start
node index.js               # Direct execution
```

### Database Requirements

- MongoDB instance (local or cloud)
- Update `MONGO_URI` in `.env` file with your connection string
- Default port is 8080 (configurable via `PORT` environment variable)

## API Structure

The API follows RESTful conventions with JSON request/response format. All address objects contain:

- `_id`: MongoDB ObjectId (auto-generated)
- `title`: String (required)
- `description`: String (required)

## CORS Configuration

The application is configured to accept requests from `http://localhost:3000` by default, suggesting it's designed to work with a frontend application running on port 3000.

## Error Handling

Controllers implement basic try-catch error handling with standard HTTP status codes:

- 200: Success
- 201: Created
- 400: Bad Request (missing fields, invalid data)
- 404: Not Found

## Database Schema

The Address model uses Mongoose with required field validation for both `title` and `description` fields.
