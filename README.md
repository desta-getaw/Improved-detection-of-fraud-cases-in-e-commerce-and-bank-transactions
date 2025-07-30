# 🕵️‍♂️ Improved Detection of Fraud in E-commerce and Bank Transactions

## 📌 Overview

This project focuses on enhancing the detection of fraudulent activities in e-commerce and credit card transactions by combining robust data preprocessing, exploratory data analysis (EDA), feature engineering, machine learning models, and explainability techniques. It integrates transaction and geolocation data to develop reliable fraud detection systems and deploys models via a Flask API.

---

## 📂 Table of Contents

- [Overview](#-overview)
- [Project Structure](#-project-structure)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
- [Data Preprocessing & Analysis](#-data-preprocessing--analysis)
- [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
- [Geolocation Analysis](#-geolocation-analysis)
- [Model Building & Training](#-model-building--training)
- [Model Explainability](#-model-explainability)
- [Deployment](#-deployment)
- [Contributors](#-contributors)
- [License](#-license)

---

## 📁 Project Structure

```
fraud_detection/
├── data/
│   ├── raw/                  # Original datasets
│   └── processed/            # Cleaned and transformed data
├── notebooks/                # Jupyter notebooks for EDA, modeling, explainability
├── models/                   # Trained model files
├── src/                      # Source scripts for preprocessing and merging
├── api/                      # Flask API and Docker configuration
├── tests/                    # Unit tests
├── mlruns/                   # MLflow tracking
├── .github/workflows/        # CI workflows
├── README.md
└── setup.py
```

---

## ⚙️ Requirements

- Python 3.10+
- Libraries:
  - `pandas`, `matplotlib`, `seaborn`, `ipaddress`
  - `scikit-learn`, `imbalanced-learn`
  - `mlflow`, `shap`, `lime`
  - `flask`, `joblib`

---

## 💻 Installation

```bash
git clone https://github.com/desta-getaw/Improved-detection-of-fraud-cases-in-e-commerce-and-bank-transactions.git
cd fraud-detection
python -m venv venv
source venv/bin/activate    # On Windows: .\venv\Scripts\activate
pip install -r requirements.txt
```

---

## ▶️ Usage

1. Add raw data to `data/raw`:
   - `Fraud_Data.csv`
   - `creditcard.csv`
   - `IpAddress_to_Country.csv`

2. Launch the analysis notebook:
   ```bash
   jupyter notebook notebooks/01_data_analysis.ipynb
   ```

---

## 🧹 Data Preprocessing & Analysis

Key preprocessing steps:
- Remove duplicates and handle missing values
- Normalize features like `purchase_value`, `Amount`
- Merge datasets using IP address ranges
- Save results to `data/processed/`

---

## 📊 Exploratory Data Analysis (EDA)

Visual analyses include:
- Histograms and boxplots of `purchase_value` by class
- Correlation heatmaps
- Country-level fraud distribution

---

## 🌐 Geolocation Analysis

- IPs converted to integers for merging
- Fraud records enriched with country data
- Visual breakdown of fraud by geography

---

## 🧠 Model Building & Training

Steps:
- Feature engineering from timestamps (e.g., `signup_hour`)
- Categorical encoding and train-test split
- Algorithms tested:
  - Logistic Regression
  - Decision Tree
  - Random Forest
  - Gradient Boosting
  - Multi-layer Perceptron (MLP)

📌 **MLflow UI**: Track experiments via:
```bash
mlflow ui
```

### 📈 Sample Performance (F1-Score on Class 1)

| Model              | Fraud Data | Credit Card Data |
|-------------------|------------|------------------|
| Logistic Regression | 0.00     | 0.70             |
| Decision Tree       | 0.57     | 0.68             |
| Random Forest       | 0.70     | 0.84             |
| Gradient Boosting   | 0.70     | 0.74             |
| MLP                 | 0.22     | 0.02             |

---

## 🧾 Model Explainability

Explainable AI techniques used:
- **SHAP**: Global and local feature importance
- **LIME**: Local interpretation for individual predictions

📁 Key Notebook: `notebooks/model_explainability.ipynb`

🧪 Plots generated:
- SHAP: Summary, force, dependence plots
- LIME: Local prediction explanations

---

## 🚀 Deployment

### 1. Flask API

- REST API to serve predictions using the trained model
- Routes:
  - `/`: Web form
  - `/predict`: Accepts input, returns prediction

### 2. Dockerization

- Dockerfile included for containerized deployment

```bash
docker build -t fraud-api .
docker run -p 5000:5000 fraud-api
```

🔗 Visit: `http://localhost:5000/`

---

## 👥 Contributors

- [Desta Getaw](https://github.com/desta-getaw)

---

## 📄 License

This project is licensed under the MIT License. See `LICENSE` file for details.
