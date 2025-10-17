# Path and Query Parameters in FastAPI  

##  Introduction  
In FastAPI, parameters are used to pass information to API endpoints.  
There are two main types of parameters:  
- **Path Parameters** → Required values that identify specific resources.  
- **Query Parameters** → Optional values used for filtering, sorting, or extra options.  

---

##  Path Parameters  

Path parameters are part of the **URL path** and are used to access specific items or resources.  

###  Example
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/patients/{patient_id}")
def get_patient(patient_id: str):
    return {"patient_id": patient_id}

How it works:
The {patient_id} part is a dynamic value in the URL.
When you visit /patients/123, the endpoint returns:
{"patient_id": "123"}


Use Case:
/users/{id} → Get details of a user by ID
/orders/{order_id} → Retrieve details of a specific order
```
# Query Parameters

Query parameters are passed after a “?” in the URL and are optional.
They are typically used for filtering, sorting, or pagination.

Example
```python
@app.get("/patients")
def get_patients(sort_by: str = "age", order: str = "asc"):
    return {"sort_by": sort_by, "order": order}
    
Usage:
/patients?sort_by=weight&order=desc

Response:
{"sort_by": "weight", "order": "desc"}
```
# Multiple Query Parameters

You can include multiple optional parameters easily:
```python
@app.get("/search")
def search_data(name: str = None, city: str = None, limit: int = 10):
    return {"name": name, "city": city, "limit": limit}
URL Example:
/search?name=John&city=London&limit=5

```
```
| Feature         | Path Parameter               | Query Parameter                  |
| --------------- | ---------------------------- | -------------------------------- |
| **Purpose**     | Identify a specific resource | Filter or modify results         |
| **Required?**   | Yes                          | No                               |
| **Example URL** | `/patients/123`              | `/patients?sort=age`             |
| **Use Case**    | Get a single record          | Get multiple or filtered records |
```

Combining Path & Query Parameters

You can use both together for more flexibility.
```python
@app.get("/patients/{patient_id}")
def get_patient(patient_id: str, details: bool = False):
    if details:
        return {"patient_id": patient_id, "details": "Full data"}
    return {"patient_id": patient_id, "details": "Basic data"}
```

# Key Takeaways

Path parameters → used to access a specific item (mandatory).

Query parameters → used for filtering or modifying the response (optional).

You can combine both to create powerful, flexible endpoints.

Always validate query inputs to avoid unexpected errors.
