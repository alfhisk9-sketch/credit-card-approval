# 💳 AI-Based Credit Card Approval Prediction System

### Powered by IBM Watson Machine Learning  
### SmartBridge AI & ML Internship Project

<div align="center">

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.0.3-000000?style=for-the-badge&logo=flask&logoColor=white)
![IBM Watson](https://img.shields.io/badge/IBM_Watson-ML-054ADA?style=for-the-badge&logo=ibm&logoColor=white)
![scikit-learn](https://img.shields.io/badge/Scikit--Learn-1.5-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)

**A machine learning web application that predicts whether a credit card application is likely to be approved or rejected by analyzing customer financial and personal information.**

[Live Demo](#) • [Documentation](#) • [Report Bug](#) • [Request Feature](#)

</div>

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Problem Statement](#-problem-statement)
- [Objectives](#-objectives)
- [Features](#-features)
- [Technology Stack](#-technology-stack)
- [Machine Learning Models](#-machine-learning-models)
- [Input Features](#-input-features)
- [Project Structure](#-project-structure)
- [Team Members](#-team-members)
- [Internship Details](#-internship-details)
- [Installation](#-installation)
- [Environment Configuration](#-environment-configuration)
- [How to Run](#-how-to-run)
- [Deployment](#-deployment)
- [Project Workflow](#-project-workflow)
- [Documentation Folder](#-documentation-folder)
- [Future Enhancements](#-future-enhancements)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

---

## 📌 Project Overview

The **AI-Based Credit Card Approval Prediction System** is an end-to-end machine learning web application developed as part of the **SmartBridge AI & Machine Learning Internship Program**.

The system predicts whether a credit card application should be **Approved** or **Rejected** by analyzing customer information such as income, employment status, credit history, education, marital status, and other financial indicators.

The best-performing model is integrated with a **Flask web application** and deployed using **IBM Watson Machine Learning** for cloud-based prediction.

---

## 🎯 Problem Statement

In traditional financial workflows, credit card approval decisions often take time and may involve manual review. This can be slow, inconsistent, and dependent on subjective evaluation.

This project aims to automate the approval prediction process using machine learning so that:

- Decisions become faster
- Predictions become more consistent
- Risk evaluation becomes more data-driven
- The system can support financial institutions in pre-screening applications

---

## 🎯 Objectives

- Build a machine learning model for credit card approval prediction
- Train and evaluate multiple classification algorithms
- Deploy the final model using IBM Watson Machine Learning
- Create a responsive Flask web application for real-time prediction
- Provide analytics and visualization for better interpretation
- Prepare professional documentation for SmartBridge internship submission

---

## ✨ Features

| Feature | Description |
|--------|-------------|
| 🔮 Real-Time Prediction | Predicts approval status instantly from user input |
| ☁ Cloud ML Integration | Uses IBM Watson Machine Learning for deployment |
| 📊 Dashboard | Displays analytics and visual insights |
| 🤖 Multiple ML Models | Trains and compares several classification algorithms |
| 📱 Responsive UI | Works on desktop and mobile devices |
| 🔒 Validation | Checks input data before prediction |
| ⚡ Fast Backend | Flask-based lightweight and efficient server |
| 🧾 Documentation | Includes SmartBridge phase-wise documentation |
| 🧪 Testing | Supports project validation and quality checks |

---

## 🛠️ Technology Stack

| Layer | Technology |
|------|------------|
| Programming Language | Python 3.11+ |
| Backend Framework | Flask 3.0.3 |
| Frontend | HTML5, CSS3, Bootstrap 5, JavaScript |
| Machine Learning | Scikit-Learn, Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Model Serialization | Joblib |
| Database | SQLite |
| Cloud Deployment | IBM Watson Machine Learning |
| Version Control | Git, GitHub |
| Hosting | Render |

---

## 🤖 Machine Learning Models

The project evaluates multiple classification algorithms to determine the best-performing model.

| Model | Purpose |
|------|---------|
| Decision Tree | Easy-to-interpret baseline classifier |
| Random Forest | Ensemble learning with improved stability |
| Logistic Regression | Strong baseline for binary classification |
| Support Vector Machine | Margin-based classification |
| Naive Bayes | Probabilistic classification |
| K-Nearest Neighbors | Instance-based classification |

### Primary Model
The final selected model is the one with the best validation performance and is deployed for prediction through IBM Watson Machine Learning.

---

## 📊 Input Features

The model uses customer-related features such as:

- Age
- Gender
- Marital Status
- Education
- Employment Status
- Years Employed
- Annual Income
- Total Assets
- Total Debt
- Credit Score
- Loan Amount
- Loan Purpose
- Loan Term
- Previous Defaults
- Previous Loans
- Customer History

---

## 📁 Project Structure

```text
credit-card-approval/
│
├── app/
│   ├── static/
│   ├── templates/
│   ├── __init__.py
│   ├── routes.py
│   └── utils.py
│
├── instance/
├── ml_models/
├── tests/
├── docs/
│   ├── diagrams/
│   ├── screenshots/
│   ├── report/
│   └── presentation/
│
├── SmartBridge-Documentation/
│   ├── 1. Brainstorming & Ideation/
│   ├── 2. Requirement Analysis/
│   ├── 3. Project Design Phase/
│   ├── 4. Project Planning Phase/
│   ├── 5. Project Development Phase/
│   ├── 6. Project Testing/
│   ├── 7. Project Documentation/
│   └── 8. Project Demonstration/
│
├── config.py
├── run.py
├── requirements.txt
├── .env.example
└── README.md


| Team Member                     | Role                                                  | Responsibilities                                                                                                                                                         |
| ------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **SK Alfhi**                    | **Application Builder & Frontend Developer**          | Flask application development, UI implementation, model integration, IBM Watson integration, Render deployment, GitHub repository management, documentation coordination |
| **SK Rabbani**                  | **Machine Learning Engineer**                         | Data preprocessing, feature engineering, algorithm selection, model training, hyperparameter tuning, evaluation, model saving                                            |
| **Bheemuni Pujitha**            | **Team Lead • Data Analyst • Visualization Engineer** | Team coordination, requirement analysis, exploratory data analysis, data visualization, reporting, documentation review                                                  |
| **Darla Krishna**               | **Data Collection Specialist**                        | Dataset collection, data verification, missing value analysis, dataset preparation, data documentation                                                                   |
| **Modugumudi TwineMallikadevi** | **Testing & Quality Assurance Engineer**              | Functional testing, integration testing, UI testing, validation testing, bug reporting, documentation verification

                                                     |
🏫 Internship Details

Internship Program: SmartBridge AI & Machine Learning Internship
Project Title: AI-Based Credit Card Approval Prediction System
Domain: Artificial Intelligence • Machine Learning • Generative AI
Project Type: End-to-End ML Web Application

⚙️ Installation
1. Clone the Repository
git clone https://github.com/alfhisk9-sketch/credit-card-approval.git
cd credit-card-approval
2. Create Virtual Environment
python -m venv venv
3. Activate Virtual Environment
Windows
venv\Scripts\activate
Linux / macOS
source venv/bin/activate
4. Install Dependencies
pip install -r requirements.txt
🔐 Environment Configuration

Create a .env file in the root directory:

SECRET_KEY=your-secret-key
DATABASE_URL=sqlite:///instance/credit_approval.db

WATSON_API_KEY=your-api-key
WATSON_URL=https://us-south.ml.cloud.ibm.com
WATSON_SPACE_ID=your-space-id
WATSON_DEPLOYMENT_ID=your-deployment-id
Environment Variables Explanation
Variable	Purpose
SECRET_KEY	Flask secret key for session/security
DATABASE_URL	Path to SQLite database
WATSON_API_KEY	IBM Watson API authentication
WATSON_URL	IBM Watson service endpoint
WATSON_SPACE_ID	Watson deployment space ID
WATSON_DEPLOYMENT_ID	Watson deployed model identifier
▶️ How to Run
python run.py

Then open your browser and visit:

http://localhost:5000
☁ Deployment
IBM Watson Machine Learning

The trained model is deployed to IBM Watson Machine Learning for cloud inference.

Render Deployment

The Flask app can be deployed on Render using:

requirements.txt
config.py
environment variables
run.py
Typical Deployment Steps
Push code to GitHub
Connect GitHub repo to Render
Set environment variables
Deploy the web service
Verify application and model endpoint
🔄 Project Workflow
User Inputs Customer Details
            ↓
Form Validation
            ↓
Data Preprocessing
            ↓
Feature Engineering
            ↓
Model Inference
            ↓
IBM Watson Prediction
            ↓
Approval / Rejection Result
            ↓
Dashboard / Analytics View
📚 Documentation Folder

The repository contains a separate documentation folder for SmartBridge submission:

SmartBridge-Documentation/
├── 1. Brainstorming & Ideation/
├── 2. Requirement Analysis/
├── 3. Project Design Phase/
├── 4. Project Planning Phase/
├── 5. Project Development Phase/
├── 6. Project Testing/
├── 7. Project Documentation/
└── 8. Project Demonstration/

This folder includes phase-wise reports, planning material, testing notes, and final project documentation.

📈 Results

The system successfully demonstrates:

Automated approval prediction
Cloud-based model inference
Responsive user interface
Practical machine learning workflow
Documentation-ready internship project structure
🚀 Future Enhancements
Add more advanced ensemble models
Improve feature engineering pipeline
Include explainable AI insights using SHAP/LIME
Add authentication and user roles
Store prediction history in a database
Expand to multi-language UI support
Integrate more comprehensive analytics dashboard
Add API endpoints for third-party integration
📄 License

This project is developed for academic and internship purposes under the SmartBridge AI & Machine Learning Internship Program.

🙏 Acknowledgements

We sincerely thank:

SmartBridge for providing the internship opportunity
IBM SkillsBuild for cloud AI/ML learning support
Our mentors and faculty for guidance
Our team members for collaboration and contribution
<div align="center">
⭐ If you found this project useful, please give it a star ⭐

Made with ❤️ using Python • Flask • IBM Watson ML • Scikit-Learn • Bootstrap

</div> ```
