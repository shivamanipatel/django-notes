Django Notes App – CI/CD Project Notes (Direct Copy-Paste)
🔹 Project Name: Django Notes App
🔹 Tech Stack: Django, Python 3.10, Jenkins, Docker, Docker Hub, AWS EC2 (Ubuntu)
✅ 1. Project Overview
This project deploys a Django Notes App using a fully automated CI/CD pipeline:

Code pushed to GitHub

Jenkins agent pulls the code and builds a Docker image

Image is pushed to Docker Hub

EC2 server automatically pulls the latest image and deploys the container

Website runs on EC2 public IP:8000

✅ 2. Pipeline Stages (Jenkinsfile)
Clone GitHub Repo

Build Docker Image

Tag Docker Image

Push Image to Docker Hub

Stop Old Container in EC2

Run New Container

Auto Deploy

✅ 3. Manual Commands Used
Docker Build & Run
bash
Copy code
docker build -t django-notes .
docker run -d -p 8000:8000 django-notes
Docker Push (Jenkins Automated)
bash
Copy code
docker tag django-notes shivamanipatelpathi/django-notes
docker push shivamanipatelpathi/django-notes
EC2 Deployment
bash
Copy code
docker stop django-notes || true
docker rm django-notes || true
docker pull shivamanipatelpathi/django-notes
docker run -d -p 8000:8000 --name django-notes shivamanipatelpathi/django-notes
✅ 4. Django Fixes Applied
Added EC2 Public IP to ALLOWED_HOSTS
ini
Copy code
ALLOWED_HOSTS = ['44.196.155.77', 'localhost', '127.0.0.1', '*']
Added Template Support
ini
Copy code
TEMPLATES = [
    {
        'DIRS': ['/app/templates'],
        'APP_DIRS': True,
    }
]
Created home.html
arduino
Copy code
/app/templates/home.html
✅ 5. Where Everything Runs
Jenkins Master: 34.198.x.x

Jenkins Agent (Build + Deploy): 44.196.x.x

Django App: http://44.196.155.77:8000

✅ 6. Docker Hub Link
Your Docker Image:
👉 https://hub.docker.com/r/shivamanipatelpathi/django-notes

✅ 7. GitHub Repo
👉 https://github.com/shivamanipatel/django-notes
