# 💳 Credit Card Approval Prediction

### Powered by IBM Watson Machine Learning

<div align="center">

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.0.3-000000?style=for-the-badge\&logo=flask\&logoColor=white)
![IBM Watson](https://img.shields.io/badge/IBM_Watson-ML-054ADA?style=for-the-badge\&logo=ibm\&logoColor=white)
![scikit-learn](https://img.shields.io/badge/Scikit--Learn-1.5-F7931E?style=for-the-badge\&logo=scikit-learn\&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge\&logo=bootstrap\&logoColor=white)

**A production-grade Credit Card Approval Prediction System using Machine Learning, Flask, and IBM Watson Machine Learning.**

[Live Demo](#) • [Documentation](#) • [Report Bug](#) • [Request Feature](#)

</div>

---

# 📌 Project Overview

This project predicts whether a credit card application will be **Approved** or **Rejected** using multiple Machine Learning algorithms. The best-performing model is deployed on **IBM Watson Machine Learning** for real-time cloud inference.

The application demonstrates an end-to-end AI/ML workflow including:

* Data Collection & Preprocessing
* Feature Engineering
* Model Training & Evaluation
* IBM Watson ML Deployment
* Flask Web Application
* Analytics Dashboard
* Prediction History
* Modern Responsive UI

---

# ✨ Features

| Feature                 | Description                                                 |
| ----------------------- | ----------------------------------------------------------- |
| 🔮 Real-Time Prediction | Predict credit card approval using IBM Watson ML            |
| 📊 Dashboard            | Interactive analytics with charts                           |
| 📋 Prediction History   | Store and view previous predictions                         |
| 🤖 Multiple ML Models   | Random Forest, Logistic Regression, Decision Tree & XGBoost |
| ☁ IBM Watson ML         | Cloud-hosted Machine Learning deployment                    |
| 📱 Responsive UI        | Bootstrap 5 modern interface                                |
| 📈 Charts               | Interactive visualizations using Chart.js                   |
| 🔒 Secure Forms         | CSRF Protection & Validation                                |
| ⚡ Fast Performance      | Flask optimized backend                                     |
| 🌐 REST API Ready       | Easy integration with external systems                      |

---

# 🏗️ Project Structure

```text
credit_card_approval/
│
├── app/
│   ├── blueprints/
│   ├── models/
│   ├── static/
│   ├── templates/
│   └── utils/
│
├── ml_models/
├── instance/
├── migrations/
├── docs/
├── tests/
│
├── config.py
├── run.py
├── requirements.txt
└── README.md
```

---

# 🚀 Installation

## Clone Repository

```bash
git clone https://github.com/alfhisk9-sketch/credit-card-approval.git
cd credit-card-approval
```

## Create Virtual Environment

```bash
python -m venv venv
```

### Windows

```bash
venv\Scripts\activate
```

### Linux / Mac

```bash
source venv/bin/activate
```

---

## Install Requirements

```bash
pip install -r requirements.txt
```

---

## Configure Environment

Create `.env`

```env
SECRET_KEY=your-secret-key

DATABASE_URL=sqlite:///instance/credit_approval.db

WATSON_API_KEY=your-api-key
WATSON_URL=https://us-south.ml.cloud.ibm.com
WATSON_SPACE_ID=your-space-id
WATSON_DEPLOYMENT_ID=your-deployment-id
```

---

## Run Project

```bash
python run.py
```

Open

```
http://localhost:5000
```

---

# 🤖 Machine Learning Models

| Model               | Accuracy  |
| ------------------- | --------- |
| XGBoost             | **89.1%** |
| Random Forest       | 87.3%     |
| Logistic Regression | 83.2%     |
| Decision Tree       | 81.5%     |

### Primary Model

✅ XGBoost deployed on IBM Watson Machine Learning

---

# 📊 Input Features

* Age
* Gender
* Marital Status
* Education
* Employment Status
* Years Employed
* Annual Income
* Total Assets
* Total Debt
* Credit Score
* Loan Amount
* Loan Purpose
* Loan Term
* Previous Defaults
* Previous Loans
* Customer History

---

# 💻 Technology Stack

| Layer            | Technology                  |
| ---------------- | --------------------------- |
| Programming      | Python 3.11                 |
| Backend          | Flask 3                     |
| Machine Learning | Scikit-Learn                |
| Cloud            | IBM Watson Machine Learning |
| Database         | SQLite                      |
| Frontend         | HTML5, CSS3, Bootstrap 5    |
| Charts           | Chart.js                    |
| Icons            | Bootstrap Icons             |
| Version Control  | Git & GitHub                |

---

# 👥 Development Team

| Team Member                     | Role                                                            |
| ------------------------------- | --------------------------------------------------------------- |
| **SK Alfhi**                    | Application Builder & Machine Learning Model Trainer (Frontend) |
| **SK Rabbani**                  | Machine Learning Model Builder (ML Algorithm Development)       |
| **Bheemuni Pujitha**            | Team Lead, Data Visualization & Data Analysis (Analyst)         |
| **Darla Krishna**               | Data Collector (Sample Data Collector)                          |
| **Modugumudi TwineMallikadevi** | Project Linker & Plan Analyst (Backend)                         |

---
# 👨‍💻 Project Lead

###Bheemuni Pujitha

** Team Lead, Data Visualization & Data Analysis (Analyst) **

---
# 👨‍💻 Project Application builder

### SK Alfhi

**Application Builder & Machine Learning Model Trainer (Frontend)**

📧 **Email:** [alfhisk9@gmail.com](mailto:alfhisk9@gmail.com)

💼 **LinkedIn:**
https://linkedin.com/in/samadani-basheer-alfhi-shaik-60ba5630b

🐙 **GitHub:**
https://github.com/alfhisk9-sketch

---

# 📚 Internship

**SmartBridge Internship**

Domain:

> Artificial Intelligence & Machine Learning

Project:

> AI-Based Credit Card Approval Prediction using IBM Watson Machine Learning

---

# 📄 License

This project is developed for academic purposes under the **SmartBridge AIML Internship Program**.

---

<div align="center">

### ⭐ If you found this project useful, please give it a Star ⭐

Made with ❤️ using **Python • Flask • IBM Watson ML • Machine Learning**

</div>
