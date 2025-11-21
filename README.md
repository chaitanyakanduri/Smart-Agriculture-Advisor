Smart Agriculture Advisor
Technical Documentation & System Specification

Smart Agriculture Advisor is an integrated, AI-driven precision agriculture system that operationalizes supervised machine learning, deep learning, and structured data pipelines to support agronomic decision-making. The system provides crop recommendation, fertilizer optimization, and plant disease detection through a modular architecture combining classical ML algorithms, convolutional networks, and rule-based agronomic heuristics.

1. System Architecture Overview

The system follows a multi-layered architecture:

1.1 Data Layer

Raw agronomic datasets (soil NPK composition, pH, temperature, humidity, rainfall)

Crop yield datasets

Fertilizer advisory datasets

Plant disease image datasets (multi-class, leaf-level annotations)

Derived features produced via preprocessing modules (normalization, encoding, augmentation)

1.2 Model Layer

The Model Layer implements:

Classical ML models

RandomForestClassifier

DecisionTreeClassifier

Naïve Bayes

SVM

XGBoost

Deep Learning models

CNN-based classifier (PyTorch) trained on leaf disease datasets

Model persistence using Pickle (.pkl) and PyTorch (.pth)

1.3 Application Layer

Flask-based microservice backend

REST API endpoints

/predict/crop

/predict/fertilizer

/predict/disease

Web UI (HTML, CSS, JS, Bootstrap, Jinja2)

Inference modules for preprocessing and postprocessing

1.4 Deployment Layer

Supports:

Local execution (Python environment)

Cloud deployment

Heroku

AWS (EC2, Elastic Beanstalk, Lambda)

Google Cloud Run

Docker containerization

CI/CD (GitHub Actions-ready)

2. Functional Modules
2.1 Crop Recommendation Engine

Input: N, P, K, temperature, humidity, pH, rainfall
Model: Random Forest (best-performing model from benchmarking)
Output: Recommended crop label

Features:

Feature normalization

Hyperparameter tuning using Grid Search

Evaluation using accuracy, F1-score, and confusion matrix

2.2 Fertilizer Optimization Engine

Input: Soil nutrient levels + crop type
Output: Fertilizer class recommendation

This module integrates:

Crop-specific nutrient requirement mapping

Soil-plant interaction heuristics

ML classification for fertilizer selection

2.3 Plant Disease Diagnosis Engine

Input: Leaf image
Pipeline:

Image pre-processing (OpenCV)

CNN forward pass

Softmax-based multi-class classification

Disease label + mitigation guidelines

Training Details:

Augmentation: rotation, scaling, horizontal/vertical flip

Framework: PyTorch

Optimizer: Adam

Loss Function: Cross Entropy

3. Data Pipelines
3.1 Preprocessing

Handling missing values

Outlier removal

Statistical normalization

Encoding categorical features

Image augmentation

3.2 Notebook Workflows

Included Jupyter notebooks document:

Data cleaning

Model experimentation

Benchmarking comparisons

Hyperparameter search

Exporting final models

4. Directory Structure
Smart_Agriculture_Advisor/
│
├── app/
│   ├── app.py               # Flask application entrypoint
│   ├── config.py            # Environment / path config
│   ├── models/              # Persisted ML/DL models
│   ├── static/              # CSS, JS, images
│   ├── templates/           # UI templates
│   └── utils/               # Inference and preprocessing modules
│
├── backend/                 # Additional backend modules
│   ├── data/                # Processed datasets
│   ├── model_training.py    # ML training workflows
│   ├── models/              # ML and DL artifacts
│   └── requirements.txt     # Backend dependencies
│
├── frontend/                # React/JS frontend (prototype)
├── Data-raw/                # Unprocessed datasets
├── Data-processed/          # Cleaned datasets
├── models/                  # Legacy model binaries
├── notebooks/               # Training and analysis notebooks
│
├── requirements.txt         # Base dependencies
├── CONTRIBUTING.md
├── LICENSE
└── README.md

5. Local Environment Setup
5.1 Clone Repository
git clone https://github.com/chaitanyakanduri/Smart-Agriculture-Advisor.git
cd Smart-Agriculture-Advisor

5.2 Create Python Environment
conda create -n smart_agri python=3.8
conda activate smart_agri
pip install -r requirements.txt

6. Running the Application
6.1 Start Flask Server
python app/app.py

6.2 Access UI
http://localhost:5000/

7. Deployment (Production)
7.1 Docker

Dockerfile example:

FROM python:3.8
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
CMD ["python", "app/app.py"]

7.2 Cloud Deployment Options

Heroku
Uses Procfile and Runtime.txt in the repo.

AWS

To deploy on EC2: Nginx + Gunicorn setup

To deploy on Elastic Beanstalk: Zip + EB CLI workflow

Google Cloud Run
Deploy via Docker container.

8. Model Performance Summary
Crop Recommendation

Best accuracy: > 95%

Algorithms tested: RF, XGBoost, SVM, NB

Fertilizer Recommendation

Rule-based baseline augmented with ML ranking

Disease Detection (DL Model)

Testing accuracy: > 92%

Architecture: Modified CNN with ~98k parameters

9. Future Extensions

Integration with IoT soil sensors

Real-time weather data ingestion

Multilingual mobile application (Android/iOS)

Satellite-based vegetation index assessment

Reinforcement Learning for irrigation optimization

10. Citation Format (if needed)
Kamduri, V.R.R. (2025). Smart Agriculture Advisor: An AI-driven System for
Crop Recommendation, Fertilizer Optimization, and Plant Disease Detection.
GitHub Repository: https://github.com/chaitanyakanduri/Smart-Agriculture-Advisor

11. Contact

Venkata Ranga Ramanuja K Chaitanya Kamduri
Email: c_kamduri@u.pacific.edu

LinkedIn: https://linkedin.com/in/venkata-kamduri
