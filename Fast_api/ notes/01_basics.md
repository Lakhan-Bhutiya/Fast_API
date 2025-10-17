# FastAPI Basics

## Introduction
FastAPI is a modern, high-performance Python framework for building APIs.  
It is designed for speed and ease of use, leveraging **Python type hints** and **asynchronous programming**.

###  Key Features
- **High performance** – built on Starlette and Pydantic.  
- **Automatic docs** – Swagger UI and ReDoc available by default.  
- **Validation** – uses Pydantic for request/response models.  
- **Asynchronous support** – handles many requests concurrently.

---

##  Setup
```bash
pip install fastapi
pip install uvicorn

```
---

# Run the app:
```
uvicorn main:app --reload
```
---
Basic Example
```
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello FastAPI!"}
```
Access in browser:
```
 http://127.0.0.1:8000/
```

HTTP Methods:
```
---------------------------
| Method	||    Purpose   |
---------------------------
GET	    ||    Retrieve data
POST	  || 	  Create data
PUT	    ||    Update data
DELETE	||    Delete data
```
