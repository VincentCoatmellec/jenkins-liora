# Jenkins CI/CD — Flask API

A Jenkins Pipeline project: build, test, and deploy a Dockerized Flask API, automated with a declarative pipeline.

## Structure

```
.
├── app.py              # Flask API
├── test_main.py        # Unit tests
├── requirements.txt    # Python dependencies
├── Dockerfile          # Containerization
└── Jenkinsfile         # CI/CD pipeline
```

## Requirements

- Public GitHub repository
- Jenkins instance (v2.0+)
- DockerHub account (credentials stored in Jenkins Credentials)
- Docker installed on the Jenkins agent

## Pipeline

The `Jenkinsfile` defines the following stages:

| Stage | Purpose |
|-------|---------|
| **Building** | Install dependencies (`pip install -r requirements.txt`) |
| **Testing** | Run unit tests (`python -m unittest`) |
| **Deploying** | Build the Docker image and run the container on port 8000 |
| **User acceptance** | Manual approval before deploying to `main` |
| **Pushing and Merging** | Push the image to DockerHub + merge (in parallel) |
| **post** | Log out of DockerHub at the end |