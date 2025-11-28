🚀 MEAN Stack Application – CI/CD with GitHub Actions + Docker + AWS EC2

This project is a Full-Stack MEAN (MongoDB, Express, Angular, Node.js) application deployed using:

Docker Containers

GitHub Actions CI/CD Pipeline

AWS EC2 Instance

Docker Hub as image registry

The setup ensures fully automated build, test, and deployment on every push to the main branch.

📂 Project Structure
/mean-frontend
    |-- Dockerfile
    |-- src/...
/mean-backend
    |-- Dockerfile
    |-- server.js
    |-- routes/...
/.github/workflows
    |-- deploy.yml

🐳 Docker Images

Two separate Docker images are maintained:

Service	Docker Hub Image
Frontend	praveenms12/mean-frontend
Backend	praveenms12/mean-backend

Both are automatically built and pushed through GitHub Actions.

🔄 CI/CD Pipeline (GitHub Actions)

The CI/CD pipeline performs the following steps:

✔ 1. Checkout Code

Pulls the repository code for building.

✔ 2. Build Docker Images

Builds both frontend and backend Docker images.

✔ 3. Login to Docker Hub

Uses GitHub Secrets:

DOCKER_USERNAME

DOCKER_PASSWORD

✔ 4. Push Images to Docker Hub

Tags and pushes latest builds.

✔ 5. Deploy to EC2 via SSH

Connects to EC2 using EC2_SSH_KEY (stored as GitHub secret)

Pulls latest Docker images

Stops existing containers

Runs updated containers

🔧 Requirements
Local:

Node.js

Angular CLI

Docker Desktop

Git / TortoiseGit

Server (EC2):

Ubuntu

Docker CE

Docker Compose (optional)

📦 Running Locally (Development)
Backend
cd mean-backend
npm install
npm start

Frontend
cd mean-frontend
npm install
ng serve

🐳 Running with Docker (Local)
Build
docker build -t mean-frontend ./mean-frontend
docker build -t mean-backend ./mean-backend

Run
docker run -p 4200:4200 mean-frontend
docker run -p 3000:3000 mean-backend

🌐 Deployment on AWS EC2

The EC2 instance must have:

sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo usermod -aG docker ubuntu

Run the app on EC2
docker pull praveenms12/mean-frontend
docker pull praveenms12/mean-backend

docker stop frontend backend || true
docker rm frontend backend || true

docker run -d -p 4200:80 --name frontend praveenms12/mean-frontend
docker run -d -p 3000:3000 --name backend praveenms12/mean-backend

🔐 GitHub Secrets Used
Secret Name	Description
DOCKER_USERNAME	Docker Hub username
DOCKER_PASSWORD	Docker Hub access token or password
EC2_HOST	Public IPv4 of EC2
EC2_USERNAME	e.g., ubuntu
EC2_SSH_KEY	Private key content of .pem file
⭐ Features

Full MEAN stack application

Dual-container architecture

Automated CI/CD with GitHub Actions

Docker-based deployment

Smooth rolling updates on EC2

🧑‍💻 Author

Praveen MS
Python Developer → DevOps Enthusiast
Docker | GitHub Actions | AWS | MEAN Stack
