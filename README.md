# Jenkins-CICD-Task2

## Project Overview
A simple CI/CD pipeline using Jenkins and Docker.

## Tools Used
- Jenkins
- Docker
- Git and GitHub
- Nginx
- HTML

## Pipeline Stages
1. Build the Docker image.
2. Test the application using a temporary container.
3. Deploy the application on port 8081.

## Run Locally
Build: `docker build -t jenkins-cicd-task2:latest .`

Run: `docker run -d --name jenkins-cicd-task2 -p 8081:80 jenkins-cicd-task2:latest`

Open http://localhost:8081 in your browser.

## Verification
The initial Jenkins pipeline completed successfully. Build, Test, and Deploy passed, and the webpage returned the expected HTML response.

## Automatic Trigger
The pipeline polls GitHub every minute. A new commit must be pushed and another build observed to verify automatic triggering.
