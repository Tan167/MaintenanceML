# MaintenanceML — Predictive Equipment Failure Detection

End-to-end ML pipeline for multiclass equipment fault classification — from data ingestion and model training to a production-ready FastAPI web app. Includes automated CI/CD with GitHub Actions, containerized with Docker, and deployed on AWS EC2 via Amazon ECR.

---

## CI/CD Pipeline

![CI/CD Pipeline Success](docs/screenshots/pipeline-success.png)

Every push to `main` automatically:
1. Builds a Docker image
2. Pushes to Amazon ECR (`:latest` + commit SHA tag)
3. SSHs into EC2 and swaps the container with zero downtime

---

## Tech Stack

| Layer | Technology |
|---|---|
| ML Model | Scikit-learn, XGBoost |
| API | FastAPI, Uvicorn |
| Containerization | Docker, Docker Compose |
| CI/CD | GitHub Actions |
| Container Registry | Amazon ECR |
| Cloud Deployment | AWS EC2 (t2.micro) |

---

## Project Structure

```
MaintenanceML/
├── src/
│   ├── data_ingestion.py
│   ├── model_training.py
│   └── inference.py
├── artifacts/
│   ├── model.pkl
│   └── preprocessor.pkl
├── templates/
├── static/
├── app.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── .github/
    └── workflows/
        └── deploy.yml
```

---

## Local Setup

```bash
git clone https://github.com/Tan167/MaintenanceML.git
cd MaintenanceML

# Run with Docker Compose
docker compose up --build

# App at http://localhost:8080
# Health check at http://localhost:8080/health
```

---

## API Endpoints

| Endpoint | Method | Description |
|---|---|---|
| `/` | GET | Web UI — input sensor readings |
| `/predict` | POST | Returns failure classification |
| `/health` | GET | Health check |

---

## ML Model

- Multiclass fault classification — No Failure, Heat Dissipation, Power, Overstrain, Tool Wear
- Trained on AI4I 2020 Predictive Maintenance Dataset
- Metric-driven model selection using Precision, Recall and F1-score
- Model artifacts stored in `artifacts/`

---

## AWS Infrastructure

```bash
# 1. Create ECR repository
aws ecr create-repository --repository-name maintenanceml --region ap-south-1

# 2. Launch EC2 (t2.micro, Amazon Linux 2023), install Docker
sudo yum update -y && sudo yum install docker -y && sudo service docker start

# 3. Add GitHub Secrets:
#    AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, EC2_HOST, EC2_SSH_KEY
```

## GitHub Secrets Required

| Secret | Description |
|---|---|
| `AWS_ACCESS_KEY_ID` | IAM user with ECR + EC2 permissions |
| `AWS_SECRET_ACCESS_KEY` | IAM secret key |
| `EC2_HOST` | Public IP of EC2 instance |
| `EC2_SSH_KEY` | Private key (.pem) for SSH access |

---

## Screenshots

### CI/CD Pipeline — GitHub Actions
![Pipeline Success](docs/screenshots/pipeline-success.png)

### Live App on AWS EC2
*Add after UI update*

### Health Check
*Add after UI update*
