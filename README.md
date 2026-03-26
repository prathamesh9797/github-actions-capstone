# GitHub Actions Capstone

A complete CI/CD pipeline built using GitHub Actions, Docker, and scheduled health checks.

---

## Workflow Status

![PR Pipeline](https://github.com/prathamesh9797/github-actions-capstone/actions/workflows/pr-pipeline.yml/badge.svg)

![Main Pipeline](https://github.com/prathamesh9797/github-actions-capstone/actions/workflows/main-pipeline.yml/badge.svg)

![Health Check](https://github.com/prathamesh9797/github-actions-capstone/actions/workflows/health-check.yml/badge.svg)

---

## Project Overview

This project is an end-to-end CI/CD pipeline built using GitHub Actions and Docker.

It demonstrates:
- Reusable workflows for build and test
- Automated Docker image build and push
- Deployment workflow using GitHub Actions
- Scheduled health checks using cron jobs

The application is a simple Flask API with a `/health` endpoint used to validate deployments.


---

##  Pipeline Flow

### Pull Request
PR opened  
→ Build & Test  
→ PR checks pass 

### Main Branch
Merge to main  
→ Build & Test  
→ Docker Build & Push  
→ Deploy 

### Scheduled Job
Every 12 hours  
→ Pull Docker image  
→ Run container  
→ Health check  
→ Report generated 

---

## Run the Project Locally

### 1. Clone the Repository
bash
git clone https://github.com/prathamesh9797/github-actions-capstone.git

cd github-actions-capstone

### 2. Create virtual environment
python -m venv venv

source venv/bin/activate   # Linux/Mac

OR

venv\Scripts\activate      # Windows

### 3. Install dependencies

pip install -r requirements.txt

### 4. Run the Application

python app/app.py

### 5. Test the App

Open in Browser

http://localhost:5000/health

Expected Response

{"status": "ok"}

## Run With Docker

### Build Image

docker build -t myapp .

### Run Container

docker run -p 5000:5000 myapp

### Test 
http://localhost:5000/health

---

## How CI/CD Workflow Works
 Pull Requests trigger **build and test only**
- Push to `main` triggers:
  - Build & Test
  - Docker Build & Push
  - Deployment
- A scheduled workflow runs every 12 hours to:
  - Pull the latest image
  - Run the container
  - Perform a health check
  - Generate a report

---

##  Future Improvements

- Slack notifications on failure
- Multi-environment deployment (dev/staging/prod)
- Rollback strategy
- Kubernetes deployment

