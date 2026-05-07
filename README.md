# 🔧 MaintenanceML — Predictive Maintenance MLOps Pipeline

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python)
![MLflow](https://img.shields.io/badge/MLflow-2.5.0-orange?style=for-the-badge&logo=mlflow)
![FastAPI](https://img.shields.io/badge/FastAPI-0.103.1-green?style=for-the-badge&logo=fastapi)
![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED?style=for-the-badge&logo=docker)
![scikit-learn](https://img.shields.io/badge/Scikit--Learn-1.4.2-F7931E?style=for-the-badge&logo=scikit-learn)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

---

## 📌 Overview

**MaintenanceML** is a production-ready **MLOps pipeline** for **Predictive Maintenance** in industrial systems. It predicts equipment failures before they happen — reducing downtime, cutting maintenance costs, and improving operational efficiency.

This project demonstrates a full end-to-end MLOps workflow: from raw sensor data ingestion and model training with experiment tracking, to a containerized web application for real-time predictions.

---

## ✨ Key Features

- 🔁 **Automated ML Pipeline** — End-to-end pipeline from data ingestion to model deployment
- 📊 **Experiment Tracking** — Full MLflow integration for tracking runs, metrics, and artifacts
- 🌐 **Web Application** — FastAPI-powered REST API with a clean HTML/CSS frontend
- 🐳 **Dockerized Deployment** — Fully containerized with Docker & Docker Compose
- ⚖️ **Imbalanced Data Handling** — Uses `imbalanced-learn` for robust handling of rare failure events
- ☁️ **AWS Ready** — Boto3 integration for cloud storage and deployment
- 🧪 **Testing & Linting** — pytest and flake8 for code quality

---

## 🗂️ Project Structure

```
MaintenanceML/
│
├── src/                        # Core source code
│   ├── components/             # ML pipeline components
│   ├── mlops/                  # MLOps utilities
│   ├── pipeline/               # Training & prediction pipelines
│   ├── __init__.py
│   ├── exception.py            # Custom exception handling
│   ├── logger.py               # Logging configuration
│   └── utils.py                # Utility functions
│
├── static/css/                 # Frontend styles
│   └── style.css
│
├── templates/                  # HTML templates
│   ├── home.html
│   └── index.html
│
├── app.py                      # FastAPI web application
├── run_pipeline.py             # Pipeline runner script
├── setup.py                    # Package setup
├── debug_imports.py            # Import debugging utility
├── requirements.txt            # Python dependencies
├── Dockerfile                  # Docker image config
├── docker-compose.yml          # Docker Compose config
└── .gitignore
```

---

## 🛠️ Tech Stack

| Category | Technology |
|----------|-----------|
| **Language** | Python 3.10+ |
| **ML Framework** | Scikit-Learn, imbalanced-learn |
| **Experiment Tracking** | MLflow 2.5.0 |
| **Web Framework** | FastAPI + Uvicorn |
| **Frontend** | HTML, CSS, Jinja2 |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Containerization** | Docker, Docker Compose |
| **Cloud** | AWS (Boto3) |
| **Testing** | Pytest, Flake8 |

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- Docker & Docker Compose (for containerized setup)
- Git

---

### Option 1 — Run Locally

**1. Clone the repository**
```bash
git clone https://github.com/Tan167/MaintenanceML.git
cd MaintenanceML
```

**2. Create and activate a virtual environment**
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Run the ML pipeline**
```bash
python run_pipeline.py
```

**5. Start the web application**
```bash
python app.py
```

Then open your browser at: `http://localhost:8000`

---

### Option 2 — Run with Docker

**1. Clone the repository**
```bash
git clone https://github.com/Tan167/MaintenanceML.git
cd MaintenanceML
```

**2. Build and run with Docker Compose**
```bash
docker-compose up --build
```

Then open your browser at: `http://localhost:8000`

---

## 📈 ML Pipeline Stages

```
Raw Data
   │
   ▼
Data Ingestion ──► Data Validation ──► Data Transformation
                                              │
                                              ▼
                                     Model Training
                                              │
                                              ▼
                                  MLflow Experiment Tracking
                                              │
                                              ▼
                                     Model Evaluation
                                              │
                                              ▼
                                   Model Deployment (FastAPI)
```

---

## 🔍 MLflow Experiment Tracking

After running the pipeline, launch the MLflow UI to view all experiments:

```bash
mlflow ui
```

Then visit: `http://localhost:5000`

You can track metrics, compare model runs, and manage artifacts all from the MLflow dashboard.

---

## 🌐 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Home page |
| `POST` | `/predict` | Submit sensor data for prediction |
| `GET` | `/health` | Health check endpoint |

---

## 📦 Dependencies

```
# Core ML
pandas==2.0.3
numpy==1.24.3
scikit-learn==1.4.2
imbalanced-learn==0.11.0

# Web Framework
fastapi==0.103.1
uvicorn[standard]==0.23.2
jinja2==3.1.2

# MLflow
mlflow==2.5.0

# Cloud
boto3==1.28.25

# Visualization
matplotlib==3.7.1
seaborn==0.12.2
```

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and commit: `git commit -m "Add your feature"`
4. Push to your branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Tan167**
- GitHub: [@Tan167](https://github.com/Tan167)

---

## ⭐ Show Your Support

If you found this project helpful, please give it a ⭐ on GitHub — it means a lot!

---

*Built with ❤️ using Python, MLflow, FastAPI, and Docker*
