# TODO Application — REST API

A simple and readable TODO CRUD REST API built with Django and Django REST Framework. Designed to be clean, minimal, and easy to understand.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Programming language |
| Django 6.0 | Web framework |
| Django REST Framework | REST API toolkit |
| drf-yasg | Swagger / OpenAPI documentation |
| SQLite | Database  |
| ngrok | Live endpoint tunneling for testing |

---

## To test this locally without ngrok

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd TODO_APPLICATION
```

### 2. Create and Activate Virtual Environment

```bash
# Create virtual environment
python -m venv menv

# Activate (Windows)
menv\Scripts\activate

# Activate (macOS/Linux)
source menv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run Migrations

```bash
python manage.py migrate
```

### 5. Start the Development Server

```bash
python manage.py runserver
```

The API will be available at `http://127.0.0.1:8000`

---

## API Endpoints

All task endpoints are prefixed with `/api/`.

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/tasks/` | List all tasks |
| `POST` | `/api/tasks/` | Create a new task |
| `GET` | `/api/tasks/<id>/` | Get a single task |
| `PUT` | `/api/tasks/<id>/` | Fully update a task |
| `PATCH` | `/api/tasks/<id>/` | Partially update a task |
| `DELETE` | `/api/tasks/<id>/` | Delete a task |

### Task Object

```json
{
    "id": 1,
    "title": "Buy groceries",
    "description": "Milk, eggs, and bread",
    "completed": false,
    "created_at": "2026-07-09T15:00:00Z"
}
```

### Example Requests

**Create a task:**
```bash
curl -X POST http://127.0.0.1:8000/api/tasks/ \
  -H "Content-Type: application/json" \
  -d '{"title": "Buy groceries", "description": "Milk, eggs, and bread"}'
```

**Mark a task as completed:**
```bash
curl -X PATCH http://127.0.0.1:8000/api/tasks/1/ \
  -H "Content-Type: application/json" \
  -d '{"completed": true}'
```

**Delete a task:**
```bash
curl -X DELETE http://127.0.0.1:8000/api/tasks/1/
```

---

## Swagger Documentation

Interactive API documentation is available when the server is running:

| URL | Description |
|-----|-------------|
| `http://127.0.0.1:8000/swagger/` | Swagger UI (interactive) |
| `http://127.0.0.1:8000/redoc/` | ReDoc UI |

You can use the Swagger UI to explore and test all endpoints directly in your browser — no extra tools needed.

---

## Live Testing with Ngrok

To expose your local server to the internet for live testing:

1. **Start the Django server** (in one terminal):
   ```bash
   python manage.py runserver
   ```

2. **Start ngrok** (in a second terminal):
   ```bash
   ngrok http 8000
   ```

3. **Copy the forwarding URL** from ngrok (e.g., `https://abc123.ngrok-free.app`) and use it to access your live endpoints:
   - `https://abc123.ngrok-free.app/api/tasks/`
   - `https://abc123.ngrok-free.app/swagger/`

---


## PEP8 Compliance

The codebase follows [PEP8](https://peps.python.org/pep-0008/) formatting guidelines. To re-format the code at any time, run:

