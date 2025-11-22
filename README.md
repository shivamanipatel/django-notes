# Django Notes App – CI/CD with Jenkins, Docker & AWS EC2

A Django notes application fully automated using Jenkins CI/CD pipeline, Docker containers, and AWS EC2 deployment.

---

## 🚀 Features

- Django application containerized using Docker
- CI/CD pipeline built with Jenkins (master–agent setup)
- Automatic Docker image build & push to Docker Hub
- Automatic deployment on AWS EC2 agent server
- Accessible from browser using EC2 public IP

---

## 🧰 Tech Stack

- **Django 5**
- **Python 3.10**
- **Docker & Docker Hub**
- **Jenkins (Master–Agent)**
- **AWS EC2 (Ubuntu)**
- **GitHub**

---

## 🧪 CI/CD Stages (from Jenkinsfile)

1. Clone GitHub repository  
2. Build Docker image  
3. Push image to Docker Hub  
4. Stop old container  
5. Start new container on EC2  

---

## 📦 Run Locally

```bash
git clone https://github.com/shivamanipatel/django-notes.git
cd django-notes
docker build -t django-notes .
docker run -d -p 8000:8000 django-notes
