# CI/CD Final Project — Counter Service

## Project name
**CI/CD Tools and Practices Final Project**

## Project overview
This repository contains a Flask-based Counter REST API used to demonstrate continuous integration and continuous delivery (CI/CD). The service exposes health and counter endpoints and is packaged in a Docker image for deployment to OpenShift.

## Technology stack
- Python 3.9 and Flask
- GitHub Actions for continuous integration
- Flake8 for linting
- Nose for unit tests
- Tekton Tasks and OpenShift Pipelines for delivery
- Docker for containerization

## API endpoints
| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Service information |
| GET | `/health` | Health check |
| GET | `/counters` | List counters |
| POST | `/counters/{name}` | Create a counter |
| GET | `/counters/{name}` | Read a counter |
| PUT | `/counters/{name}` | Increment a counter |
| DELETE | `/counters/{name}` | Delete a counter |

## Run locally
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python -m flask --app service run --host=0.0.0.0 --port=8000
```

## Run quality checks and tests
```bash
flake8 service tests
nosetests -v
```

## CI/CD
GitHub Actions runs Flake8 and the Nose unit-test suite on pushes and pull requests. Tekton task definitions are maintained in `.tekton/tasks.yml` for cleanup and test execution. OpenShift Pipeline resources and cluster-specific evidence are created in the lab environment.

## Author
Smayan Salunkhe
