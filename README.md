# Django Notes App – CI/CD with Jenkins, Docker & AWS EC2 🚀

A small Django Notes application fully automated using modern DevOps tools: **Jenkins**, **Docker**, **Docker Hub**, and **AWS EC2**.

---

## 🌐 Live Demo  
[http://44.196.155.77:8000](http://44.196.155.77:8000)  
*(Application deployment via CI/CD pipeline)*

---

## 🧰 Tech Stack  

| Component         | Tool/Platform                  |
|-------------------|-------------------------------|
| Web Framework     | Django 5 (Python 3.10)        |
| Containerization  | Docker                        |
| Image Registry    | Docker Hub (`shivamanipatelpathi/django-notes`) |
| CI/CD Tool        | Jenkins (Master–Agent on AWS) |
| Cloud Platform    | AWS EC2 (Ubuntu)              |
| Version Control   | Git & GitHub                  |

---

## 🔄 CI/CD Pipeline Overview  

1. GitHub commit → triggers Jenkins pipeline.  
2. Jenkins (Agent) builds a Docker image (`django-notes`).  
3. The image is tagged and pushed to Docker Hub.  
4. On the AWS EC2 agent node, old container is stopped and removed.  
5. New container is run (port 8000 exposed) with latest image.  
6. User accesses the live app publicly via EC2 public IP.

**Pipeline Stages in `Jenkinsfile`:**  
- Clone Repo  
- Build Docker Image  
- Login to Docker Hub  
- Push Docker Image  
- Deploy Container

---

## 🐳 Quick Start (Run locally)  

```bash
git clone https://github.com/shivamanipatel/django-notes.git
cd django-notes

# build docker image
docker build -t django-notes .

# run container
docker run -d -p 8000:8000 django-notes

# open browser
http://localhost:8000

