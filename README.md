# Todo-SQLite Service

## Overview
The `todo_app` service is a backend API for managing tasks. It uses SQLite as its database and provides a RESTful API to perform CRUD (Create, Read, Update, Delete) operations on tasks.

## Features
- Create tasks with a title and description.
- Mark tasks as completed or not completed.
- Retrieve all tasks or a single task by ID.
- Update and delete tasks.

## Prerequisites
- **Python 3.9+**
- **Pip**: [Install Pip](https://pip.pypa.io/en/stable/installation/)
- **Docker (optional)**: For containerized deployment.

## API Endpoints
### Base URL
- Default: `http://localhost:8000`

### Endpoints
1. **Get All Tasks**
   - **GET** `/items`
   - Response:
     ```json
     [
       {
         "id": 1,
         "title": "Sample Task",
         "description": "This is a task description.",
         "completed": false
       }
     ]
     ```

2. **Get a Single Task**
   - **GET** `/items/{item_id}`
   - Response:
     ```json
     {
       "id": 1,
       "title": "Sample Task",
       "description": "This is a task description.",
       "completed": false
     }
     ```

3. **Create a Task**
   - **POST** `/items`
   - Request Body:
     ```json
     {
       "title": "New Task",
       "description": "Details about the task",
       "completed": false
     }
     ```
   - Response:
     ```json
     {
       "id": 2,
       "title": "New Task",
       "description": "Details about the task",
       "completed": false
     }
     ```

4. **Update a Task**
   - **PUT** `/items/{item_id}`
   - Request Body:
     ```json
     {
       "title": "Updated Task",
       "description": "Updated details about the task",
       "completed": true
     }
     ```
   - Response:
     ```json
     {
       "id": 1,
       "title": "Updated Task",
       "description": "Updated details about the task",
       "completed": true
     }
     ```

5. **Delete a Task**
   - **DELETE** `/items/{item_id}`
   - Response:
     ```json
     {
       "message": "Item deleted"
     }
     ```

## Installation and Setup

### Local Setup
1. **Clone the repository**:
   ```bash
   git clone https://github.com/ivr0ma/todo_app.git
   cd todo_app
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**:
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000
   ```

4. **Access the API**:
   Open your browser or API client (e.g., Postman) and navigate to `http://localhost:8000/docs` for API documentation.

### Docker Setup

1. **Build the Docker image**:
   ```bash
   docker build -t todo_sqlite:latest .
   ```

2. **Run the container**:
   ```bash
   docker run -d --name todo_sqlite -p 8000:80 -v todo_data:/app/data todo_sqlite:latest
   ```

3. **Access the API**:
   Open your browser or API client and navigate to `http://localhost:8000/docs` for API documentation.
