Let's build a REST API using **Python + FastAPI**.

FastAPI is lightweight, supports asynchronous endpoints, automatically generates API documentation, and works well for AI/ML backends.

## 1. Install dependencies

```bash
pip install fastapi uvicorn
```

## 2. Project structure

```text
python-api/
├── main.py
└── requirements.txt
```

## 3. Create `main.py`

```python
# main.py

from fastapi import FastAPI

app = FastAPI(
    title="Python API",
    description="A simple REST API",
    version="1.0.0"
)

# Home endpoint
@app.get("/")
def home():
    return {"message": "API is running"}

# GET endpoint
@app.get("/users")
def get_users():
    return [
        {"id": 1, "name": "Alex"},
        {"id": 2, "name": "Jordan"}
    ]

# GET endpoint with parameter
@app.get("/users/{user_id}")
def get_user(user_id: int):
    return {
        "user_id": user_id,
        "status": "found"
    }

# POST endpoint
@app.post("/users")
def create_user(name: str):
    return {
        "message": "User created",
        "name": name
    }
```

## 4. Run the API

```bash
uvicorn main:app --reload
```

Your API runs at:

```text
http://127.0.0.1:8000
```

## 5. Test the endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/` | Home |
| GET | `/users` | List users |
| GET | `/users/1` | Get user |
| POST | `/users?name=Alex` | Create user |

## 6. Automatic API documentation

FastAPI generates interactive documentation automatically.

Open:

```text
http://127.0.0.1:8000/docs
```

You can test your endpoints directly in your browser.

## 7. Connect a frontend

Your React application can communicate with Python:

```javascript
// Fetch data from Python API

async function getUsers() {
    const response = await fetch(
        "http://127.0.0.1:8000/users"
    );

    const data = await response.json();

    console.log(data);
}

getUsers();
```

**Architecture:**

```text
React / TypeScript
       |
       | HTTP requests
       v
Python / FastAPI
       |
       v
Business Logic
       |
       v
Database / AI Model
```

**Next step:** Build a more complete Python API with authentication, SQLite, CRUD operations, API keys, and AI model inference.