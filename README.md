# nextjs-docker-ec2

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazon-aws&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=next.js&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=github-actions&logoColor=white)

> Dockerized Next.js app deployed to AWS EC2 with automated GitHub Actions CI/CD pipeline.

---

## 📌 Project Overview

iTasks is a productivity task management app built with Next.js. This repo demonstrates how to containerize a Next.js application using Docker and deploy it to AWS EC2 with a fully automated CI/CD pipeline using GitHub Actions.

Every `git push` to `main` automatically deploys to production — zero manual work.

---

## 🏗️ Architecture
Developer
↓
git push origin main
↓
GitHub Actions triggers
↓
SSH into AWS EC2
↓
Docker build + run
↓
Live at http://EC2-IP:3000
---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Next.js 16 | Frontend framework |
| Docker | Containerization |
| AWS EC2 | Cloud server |
| GitHub Actions | CI/CD pipeline |
| Bash | Automation script |

---

## 🚀 Getting Started

### Prerequisites
- Node.js 20+
- Docker
- AWS account

### Run Locally
```bash
git clone https://github.com/Nafiz-Howladar/nextjs-docker-ec2.git
cd nextjs-docker-ec2
npm install
npm run dev
```

Open `http://localhost:3000`

### Run with Docker
```bash
docker build -t itasks .
docker run -d -p 3000:3000 itasks
```

Open `http://localhost:3000`

---

## ⚙️ CI/CD Pipeline

Workflow file: `.github/workflows/deploy.yml`

### How it works:

1. Push code to `main` branch
2. GitHub Actions triggers automatically
3. SSH into EC2 server
4. Pull latest code
5. Docker build new image
6. Stop old container
7. Run new container
8. Health check passes
9. Live! ✅

### GitHub Secrets Required

| Secret | Description |
|--------|-------------|
| `EC2_HOST` | EC2 public IP address |
| `EC2_USER` | SSH username (ubuntu) |
| `EC2_KEY` | Private key (.pem file content) |

---

## 📁 Project Structure
nextjs-docker-ec2/
├── .github/
│   └── workflows/
│       └── deploy.yml    # CI/CD pipeline
├── app/                  # Next.js app directory
├── public/               # Static files
├── Dockerfile            # Multi-stage Docker build
├── .dockerignore         # Docker ignore rules
└── README.md
---

## 💡 Key Learnings

- Multi-stage Docker builds reduce final image size significantly
- GitHub Secrets keep credentials safe — never hardcode!
- `--restart always` ensures container survives server reboot
- `docker system prune` prevents disk space issues on EC2
- Always health check after deploy

---

## 🌐 Live Demo

This app is deployed on AWS EC2 using Docker and GitHub Actions CI/CD pipeline.
To run your own instance, follow the setup instructions above and deploy to any cloud server.

## 📄 License

This project is based on [iTasks](https://github.com/alsiam/iTasks) by [@alsiam](https://github.com/alsiam).
