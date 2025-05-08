# FastAPI Todo List API

A modern RESTful API for a Todo List application built with FastAPI and PostgreSQL.

## Features

- RESTful API endpoints for todo management
- PostgreSQL database for data persistence
- Pydantic schemas for request/response validation
- SQLAlchemy ORM for database operations
- Automatic OpenAPI documentation
- CORS support for frontend integration

## API Documentation

When the API is running, you can access the interactive API documentation at:
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## Prerequisites

- Python 3.8+
- PostgreSQL
- Docker (optional, for running PostgreSQL)

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/franakol/fastapi-todo-list.git
cd fastapi-todo-list
```

### 2. Set up a virtual environment

```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up PostgreSQL

You can either use an existing PostgreSQL installation or use Docker to run PostgreSQL:

```bash
docker-compose up -d
```

### 5. Configure environment variables

Create a `.env` file in the project root with the following content (adjust as needed):

```
DATABASE_URL=postgresql://postgres:postgres@localhost:5433/todo_db
```

### 6. Run the application

```bash
python main.py
```

The API will be available at http://localhost:8000

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | / | Welcome message |
| GET | /todos/ | Get all todos |
| GET | /todos/{todo_id} | Get a specific todo |
| POST | /todos/ | Create a new todo |
| PUT | /todos/{todo_id} | Update a todo |
| DELETE | /todos/{todo_id} | Delete a todo |

## Request/Response Examples

### Create a Todo

**Request:**

```json
POST /todos/

{
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "completed": false
}
```

**Response:**

```json
{
  "id": 1,
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "completed": false,
  "created_at": "2025-05-08T07:30:00.000Z",
  "updated_at": null
}
```

## Frontend Integration

This API is designed to work with the [React Todo UI](https://github.com/franakol/react-todo-ui) frontend. The frontend is configured to connect to this API at http://localhost:8000.

## Project Structure

```
/
├── main.py           # FastAPI application and endpoints
├── models.py         # SQLAlchemy ORM models
├── schemas.py        # Pydantic schemas for request/response
├── database.py       # Database connection and session
├── requirements.txt  # Python dependencies
├── docker-compose.yml # Docker configuration for PostgreSQL
└── .env              # Environment variables (not in repo)
```

## Development

### Running Tests

```bash
pip install pytest
python -m pytest
```

### Code Formatting

```bash
pip install black
black .
```

## Deployment

This API can be deployed to any platform that supports Python applications, such as:

- Heroku
- AWS Elastic Beanstalk
- Google Cloud Run
- DigitalOcean App Platform

Remember to set the appropriate environment variables for your production database.

## License

This project is licensed under the MIT License.
