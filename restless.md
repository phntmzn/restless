You can integrate **[Restless](chatgpt://generic-entity?number=0) with your Python FastAPI backend**.

Restless provides API documentation, request monitoring, traffic logging, and debugging for your existing Python API.

It supports FastAPI, Flask, Django, and Starlette. [oai_citation:0‡Restless](https://www.restless.ai/changelog/sdks-for-ruby-python-and-go?utm_source=chatgpt.com)

## 1. Project structure

```text
python-api/
├── main.py
├── requirements.txt
├── .env
└── .restless/
```

## 2. Install dependencies

```bash
pip install fastapi uvicorn restless-sdk python-dotenv
```

## 3. Initialize Restless

From your project directory:

```bash
npx restless init
```

The CLI detects your Python framework, generates an OpenAPI specification, and configures the SDK. [oai_citation:1‡Restless](https://www.restless.ai/documentation?utm_source=chatgpt.com)

## 4. Configure `main.py`

For a manual FastAPI integration:

```python
# main.py

# INSTALL:
# pip install fastapi uvicorn restless-sdk python-dotenv
#
# INITIALIZE:
# npx restless init
#
# RUN:
# uvicorn main:app --reload

import os
import restless

from fastapi import FastAPI
from dotenv import load_dotenv

load_dotenv()

# Initialize Restless
client = restless.Restless(
    os.environ["RESTLESS_KEY"]
)

# Create FastAPI application
app = FastAPI(
    title="Python REST API",
    version="1.0.0"
)

# Configure Restless request tracking
@client.setup
def setup_request(request):
    return {
        "owner": {
            "id": "default-workspace"
        }
    }

# Wrap FastAPI application
app = client.asgi(app)


# API endpoints

@app.get("/")
def home():
    return {"message": "API running"}


@app.get("/users")
def get_users():
    return [
        {"id": 1, "name": "Alex"},
        {"id": 2, "name": "Jordan"}
    ]


@app.get("/health")
def health():
    return {"status": "healthy"}
```

The SDK wraps your ASGI application and captures API traffic. [oai_citation:2‡PyPI](https://pypi.org/project/restless-sdk/)

## 5. Configure `.env`

```env
RESTLESS_KEY=your_restless_project_key
```

Keep this file out of Git.

## 6. Start your API

```bash
uvicorn main:app --reload
```

Your endpoints:

| Endpoint | Purpose |
|---|---|
| `/` | Home |
| `/users` | User data |
| `/health` | Health check |
| `/docs` | Swagger documentation |
| `/openapi.json` | OpenAPI specification |

**Resources:**

- [oai_citation:3‡restless.ai](https://www.restless.ai/documentation?utm_source=chatgpt.com)
- [oai_citation:4‡pypi.org](https://pypi.org/project/restless-sdk/)

**Important:** If you run `npx restless init`, let it configure the SDK first. Don't manually add a second integration if the CLI already wired it into your application.