# ☀️ Solar Panel Defect Classification

An end-to-end Computer Vision web application built with **Streamlit**, **TensorFlow**, and a fine-tuned **EfficientNet** deep learning model to detect and classify defects or contamination on solar photovoltaic (PV) panels.

---

## 📌 Overview

Solar panel efficiency degrades significantly when panels suffer from surface contamination (dust, snow, bird droppings) or structural/electrical failures. This project provides an intelligent inspection system that analyzes uploaded solar panel images and classifies them into one of six categories with confidence scores and top predictions.

---

## 🎯 Target Classes

The classifier distinguishes between 6 distinct conditions:
1. **Bird-drop**: Surface contamination caused by bird droppings.
2. **Clean**: Optimal panel condition with no defects.
3. **Dusty**: Dust and soil accumulation reducing solar irradiance absorption.
4. **Electrical-damage**: Internal cell or connection issues (hotspots, burn marks).
5. **Physical-damage**: Cracked glass, broken frames, or cell fractures.
6. **Snow-Covered**: Panel obstruction caused by snow layers.

---

## 📁 Project Structure

```text
├── app.py                            # Streamlit web application & inference pipeline
├── trained_effnet_finetune.h5        # Pre-trained fine-tuned EfficientNet model
├── Solar_Panel_Classification.ipynb  # Model training & fine-tuning notebook
├── requirements.txt                  # Python package dependencies
├── Dockerfile                        # Container specification
├── docker-compose.yml                # Docker Compose orchestration
├── Deployment.txt                    # EC2 / VPS manual deployment instructions
├── .dockerignore                     # Docker build exclusions
├── .gitignore                        # Git ignore rules
└── README.md                         # Documentation
```

---

## 🚀 Getting Started

### 1. Prerequisites
- Python 3.10+ (Python 3.10 or 3.11 recommended for TensorFlow)
- `pip` package manager

### 2. Setup Virtual Environment

**Windows:**
```powershell
python -m venv .venv
.venv\Scripts\activate
```

**Linux / macOS:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Streamlit Application

```bash
streamlit run app.py
```

Open your browser and navigate to `http://localhost:8501`.

---

## 🐳 Run with Docker

To build and run using Docker:

```bash
docker build -t solar-panel-defect-classifier .
docker run -p 8501:8501 solar-panel-defect-classifier
```

Or run via Docker Compose:

```bash
docker compose up -d
```

---

## ☁️ Deployment Guide

### Option 1: Streamlit Community Cloud (Recommended & Instant)
1. Push this repository to GitHub.
2. Sign in to [Streamlit Community Cloud](https://share.streamlit.io/).
3. Click **New app**, select your repository, set Main file path to `app.py`, and click **Deploy**.

### Option 2: Ubuntu / AWS EC2 Deployment
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git python3-pip python3-venv -y

git clone <YOUR_GITHUB_REPO_URL>
cd <REPO_FOLDER>

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# Run permanently in background
nohup streamlit run app.py --server.port 8501 --server.address 0.0.0.0 &
```
