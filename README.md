# DevOps CA1 – Automated CI/CD Pipeline for Containerized Applications

## Problem Statement

Develop a secure, automated CI/CD pipeline that tests, builds, and deploys a containerized web application to a Kubernetes cluster, ensuring faster and more reliable software delivery.

## Objective

Modern software teams need to deliver updates quickly and reliably without manual intervention at every step. This project demonstrates a complete DevOps workflow that automates the full lifecycle of a web application — from source code to a running deployment — using industry-standard tools.

Specifically, this project aims to:
- Automate testing so that broken code never reaches production
- Package the application consistently using containerization
- Trigger builds and tests automatically on every code change
- Deploy the application to a container orchestration platform (Kubernetes)
- Provide health checks so the system can detect and recover from failures

## Solution Overview

A Flask web application is developed, tested, containerized with Docker, and deployed to a Kubernetes cluster. A GitHub Actions pipeline automatically installs dependencies, runs tests, and builds the Docker image on every push to the `main` branch.

### Architecture
Developer
│
▼
GitHub Repository
│
▼
GitHub Actions (CI/CD)
├── Install dependencies
├── Run automated tests (pytest)
└── Build Docker image
│
▼
Docker Container
│
▼
Kubernetes Deployment
├── 2 Replicas (Pods)
├── Liveness Probe (/health)
└── NodePort Service (external access)

## Technologies Used

| Category | Technology |
|---|---|
| Backend | Python, Flask |
| Testing | Pytest |
| Containerization | Docker |
| CI/CD | GitHub Actions |
| Orchestration | Kubernetes |
| Version Control | Git, GitHub |

## Project Structure
devops-ca1-website/
├── .github/workflows/
│ └── pipeline.yml # CI/CD pipeline definition
├── static/
│ └── style.css
├── templates/
│ ├── index.html
│ └── about.html
├── tests/
│ └── test_app.py # Automated tests
├── app.py # Flask application
├── Dockerfile # Container definition
├── deployment.yaml # Kubernetes Deployment
├── service.yaml # Kubernetes Service
├── requirements.txt
└── README.md

## How to Run Locally

### 1. Clone the repository
```bash
git clone https://github.com/Bokhit235/devops-ca1-website.git
cd devops-ca1-website
```

### 2. Set up a virtual environment and install dependencies
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 3. Run the application
```bash
python app.py
```
Visit `http://localhost:5001`

### 4. Run tests
```bash
pytest tests/
```

## How to Run with Docker

```bash
docker build -t devops-ca1-website .
docker run -p 5001:5001 devops-ca1-website
```

## How to Deploy to Kubernetes

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get services
```

Access the application via the NodePort service on port `30001`.

## CI/CD Pipeline

Every push to the `main` branch automatically triggers a GitHub Actions workflow that:
1. Checks out the code
2. Sets up Python 3.11
3. Installs dependencies
4. Runs the test suite
5. Builds the Docker image

This ensures that no broken code is ever merged without being validated first.

## Endpoints

| Route | Description |
|---|---|
| `/` | Home page |
| `/about` | About the project |
| `/health` | Health check endpoint (used by Kubernetes liveness probe) |

## Team Members

- Bokhit Mahamat — Application, Testing, Docker & Documentation
- Mourno Mahamat Issack — CI/CD Pipeline (GitHub Actions) & Kubernetes Deployment

## Conclusion

This project demonstrates a complete, working DevOps pipeline covering source control, automated testing, containerization, continuous integration/continuous deployment, and container orchestration — reflecting real-world practices used by modern software engineering teams.