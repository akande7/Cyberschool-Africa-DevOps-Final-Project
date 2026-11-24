# Node.js app on AWS: Docker and GitHub Actions CI/CD

My final project for the CyberSchool Africa DevOps programme (Batch B). It containerises a Node.js/Express web app and deploys it automatically to an AWS EC2 instance on every push.

## Pipeline

```
git push (master)
      │
      ▼
GitHub Actions
 ├─ 1. Check out the code
 ├─ 2. Log in to Docker Hub (credentials stored in GitHub Secrets)
 ├─ 3. Build the Docker image from the Dockerfile
 ├─ 4. Push the image to Docker Hub
 └─ 5. SSH into the EC2 instance and run the new container
      │
      ▼
AWS EC2 (Ubuntu): app live on the instance
```

The whole workflow is defined in [`.github/workflows/dev.yaml`](.github/workflows/dev.yaml).

## Tech stack

Node.js · Express · Docker · Docker Hub · GitHub Actions · AWS EC2 · SSH

## What I practised

- Writing a Dockerfile to containerise a Node.js app
- Automating build, push and deploy with GitHub Actions
- Keeping credentials out of the code: Docker Hub and EC2 SSH details live in GitHub Secrets
- Deploying to and managing an EC2 instance over SSH

## Run locally

```bash
docker build -t sharkapp .
docker run -p 3000:3000 sharkapp   # then open http://localhost:3000
```

The sample Express app is adapted from DigitalOcean's `nodejs-image-demo` tutorial. This project focuses on the containerisation and CI/CD pipeline.
