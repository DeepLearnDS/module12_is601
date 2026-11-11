# Module 12: User & Calculation Routes + Integration Testing

## Assignment Overview

This project implements user registration and login endpoints, calculation CRUD operations, and integration testing using FastAPI, Pydantic schemas, and SQLAlchemy models.

The project also integrates automated testing and Docker Hub deployment through GitHub Actions.

## 1. User Endpoints

The application implements the following user authentication endpoints:

| Method | Endpoint | Description |
|---|---|---|
| POST | `/users/register` | Register a new user using the `UserCreate` schema |
| POST | `/users/login` | Authenticate a user by verifying hashed passwords |

## 2. Calculation Endpoints (BREAD)

The application implements the following calculation operations:

| Operation | Method | Endpoint |
|---|---|---|
| Browse | GET | `/calculations` |
| Read | GET | `/calculations/{id}` |
| Edit | PUT/PATCH | `/calculations/{id}` |
| Add | POST | `/calculations` |
| Delete | DELETE | `/calculations/{id}` |

The calculation endpoints use the existing `CalculationCreate` and `CalculationRead` Pydantic schemas and the SQLAlchemy Calculation model.

## 3. Manual Testing and OpenAPI

The endpoints can be manually tested using FastAPI OpenAPI documentation.

Access the documentation at:

- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

These interfaces allow users to submit requests and verify endpoint responses.

## 4. Integration Testing

Pytest is used to validate user and calculation functionality.

The integration tests cover:

**User Tests**
- User registration
- User login
- Password verification
- User data stored in the database

**Calculation Tests**
- Create a calculation
- Retrieve a calculation
- Update a calculation
- Delete a calculation
- Invalid input and error responses

## 5. Running Integration Tests Locally

Activate the project's virtual environment:

```bash
source venv/bin/activate
```

Run all tests:

```bash
pytest -v
```

Run integration tests:

```bash
pytest tests/integration/ -v
```

Run unit tests:

```bash
pytest tests/unit/ -v
```

Run end-to-end tests:

```bash
pytest tests/e2e/ -v
```

Make sure the PostgreSQL database is running and the test database connection is configured before running the tests.

## 6. CI/CD with GitHub Actions

GitHub Actions automates the testing and deployment process.

The workflow includes:

1. **Test:** Starts a PostgreSQL service and runs the automated test suite.
2. **Security:** Builds the Docker image.
3. **Deploy:** Pushes the Docker image to Docker Hub after the preceding jobs succeed.

The workflow runs automatically when changes are pushed to the main branch.

## 7. Docker Hub Repository

The Docker image is published to:

https://hub.docker.com/r/codeec/601_module12

Pull the image using:

```bash
docker pull codeec/601_module12:latest
```

## 8. GitHub Repository

Project repository:

https://github.com/DeepLearnDS/module12_is601

