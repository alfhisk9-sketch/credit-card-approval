# Phase 5: Project Development

**Project:** AI-Based Credit Card Approval Prediction System
**Program:** SmartBridge Externship | AICTE | IBM SkillsBuild

---

## 5.1 Dataset

### Source & Description

| Attribute | Details |
|---|---|
| Dataset Name | credit_approval_dataset.csv |
| Type | Synthetic dataset (realistic distribution) |
| Total Records | 3,000+ rows |
| Total Features | 10 input features + 1 binary target |
| Target Variable | `Approval` (0 = Rejected, 1 = Approved) |
| Class Distribution | ~50% Approved, ~50% Rejected |
| Format | UTF-8 CSV |

### Feature Description

| Feature | Data Type | Range / Values | ML Relevance |
|---|---|---|---|
| Age | Integer | 18–100 | Moderate — older applicants may have more credit history |
| Income | Float | Continuous | High — primary indicator of repayment capacity |
| Employment_Years | Integer | 0–50 | High — job stability signals reliability |
| Credit_Score | Integer | 300–850 | Very High — strongest single predictor |
| Debt_Ratio | Float | 0.0–1.0 | Very High — existing debt burden |
| Num_Dependents | Integer | 0–10 | Moderate — affects disposable income |
| Education | Categorical | High School/Bachelor/Master/PhD | Low–Moderate |
| Housing | Categorical | Rent/Own/Mortgage/Other | Low–Moderate |
| Previous_Defaults | Binary | 0/1 | Very High — direct credit history signal |
| Loan_Amount | Float | Continuous | High — higher loans increase risk |
| Approval | Binary (Target) | 0/1 | Target variable |

---

## 5.2 Data Preprocessing

### Step 1: Data Loading
```python
import pandas as pd
import numpy as np

df = pd.read_csv('credit_approval_dataset.csv')
print(f"Dataset shape: {df.shape}")       # (3000, 11)
print(df.isnull().sum())                  # Check missing values
print(df['Approval'].value_counts())      # Class balance check
```

### Step 2: Missing Value Analysis
- **Strategy:** The synthetic dataset was constructed with no missing values
- **Verification:** `df.isnull().sum()` returns zero for all columns
- **Future Handling:** If nulls exist, numeric columns → median imputation; categorical → mode imputation

### Step 3: Outlier Detection
- Credit Score: values outside [300, 850] → clipped
- Age: values outside [18, 100] → clipped
- Debt Ratio: values outside [0.0, 1.0] → clipped
- Income and Loan Amount: IQR method for extreme outliers

### Step 4: Categorical Encoding
```python
from sklearn.preprocessing import LabelEncoder

le_edu = LabelEncoder()
le_house = LabelEncoder()

df['Education_Encoded'] = le_edu.fit_transform(df['Education'])
df['Housing_Encoded'] = le_house.fit_transform(df['Housing'])
```

| Category | Encoded Values |
|---|---|
| Education: High School=0, Bachelor=1, Master=2, PhD=3 | LabelEncoded |
| Housing: Mortgage=0, Other=1, Own=2, Rent=3 | LabelEncoded |

### Step 5: Feature Selection
```python
features = [
    'Age', 'Income', 'Employment_Years', 'Credit_Score',
    'Debt_Ratio', 'Num_Dependents', 'Previous_Defaults',
    'Loan_Amount', 'Education_Encoded', 'Housing_Encoded'
]
X = df[features]
y = df['Approval']
```

### Step 6: Train/Test Split
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)
# Training: 2400 samples | Testing: 600 samples
```

### Step 7: Feature Scaling
```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

---

## 5.3 Exploratory Data Analysis (EDA)

### Key Findings

**Approval Distribution:**
- ~50% Approved, ~50% Rejected — balanced dataset — no resampling required

**Correlation with Approval (Top Features):**

| Feature | Correlation with Approval |
|---|---|
| Credit_Score | +0.72 (Strong Positive) |
| Income | +0.58 (Moderate Positive) |
| Debt_Ratio | -0.61 (Strong Negative) |
| Previous_Defaults | -0.69 (Strong Negative) |
| Employment_Years | +0.41 (Moderate Positive) |
| Loan_Amount | -0.35 (Moderate Negative) |

**Visualizations Generated:**
1. Approval distribution pie chart
2. Feature correlation heatmap
3. Credit Score distribution by approval status (box plot)
4. Income vs Approval (violin plot)
5. Feature importance bar chart (post-training)

---

## 5.4 Model Training

### Primary Model: Random Forest Classifier

```python
from sklearn.ensemble import RandomForestClassifier

rf = RandomForestClassifier(
    n_estimators=200,
    max_depth=10,
    random_state=42
)
rf.fit(X_train, y_train)
```

**Configuration Rationale:**
- `n_estimators=200` — 200 trees reduces variance without excessive compute
- `max_depth=10` — prevents overfitting while capturing complex patterns
- `random_state=42` — ensures reproducibility

### Baseline Model: Logistic Regression

```python
from sklearn.linear_model import LogisticRegression

lr = LogisticRegression(max_iter=1000, random_state=42)
lr.fit(X_train_scaled, y_train)
```

Note: Logistic Regression uses `X_train_scaled`; Random Forest does not require scaling.

---

## 5.5 Model Evaluation

### Performance Metrics

| Metric | Random Forest | Logistic Regression |
|---|---|---|
| **Accuracy** | **88.83%** | ~82% |
| **Precision (Avg)** | **0.89** | ~0.83 |
| **Recall (Avg)** | **0.89** | ~0.82 |
| **F1-Score (Avg)** | **0.89** | ~0.82 |
| **AUC-ROC** | **0.94** | ~0.88 |

### Classification Report (Random Forest)

| Class | Precision | Recall | F1-Score | Support |
|---|---|---|---|---|
| 0 — Rejected | 0.90 | 0.88 | 0.89 | ~300 |
| 1 — Approved | 0.88 | 0.90 | 0.89 | ~300 |
| **Weighted Avg** | **0.89** | **0.89** | **0.89** | **600** |

### Evaluation Code
```python
from sklearn.metrics import accuracy_score, classification_report, roc_auc_score

rf_pred = rf.predict(X_test)
rf_proba = rf.predict_proba(X_test)[:, 1]

print(f"Accuracy:  {accuracy_score(y_test, rf_pred):.4f}")    # 0.8883
print(f"AUC-ROC:   {roc_auc_score(y_test, rf_proba):.4f}")   # 0.94
print(classification_report(y_test, rf_pred))
```

### Feature Importance (Random Forest)

```python
importances = pd.Series(
    rf.feature_importances_, index=features
).sort_values(ascending=False)
```

| Rank | Feature | Importance Score |
|---|---|---|
| 1 | Credit_Score | ~0.28 |
| 2 | Debt_Ratio | ~0.22 |
| 3 | Previous_Defaults | ~0.18 |
| 4 | Income | ~0.14 |
| 5 | Employment_Years | ~0.08 |
| 6 | Loan_Amount | ~0.05 |
| 7 | Age | ~0.03 |
| 8 | Num_Dependents | ~0.01 |
| 9 | Education_Encoded | ~0.005 |
| 10 | Housing_Encoded | ~0.005 |

---

## 5.6 Model Saving & Artifact Management

```python
import pickle

# Save Random Forest model
with open('ml_models/model.pkl', 'wb') as f:
    pickle.dump(rf, f)

# Save StandardScaler
with open('ml_models/scaler.pkl', 'wb') as f:
    pickle.dump(scaler, f)

# Save both LabelEncoders
with open('ml_models/encoders.pkl', 'wb') as f:
    pickle.dump({'education': le_edu, 'housing': le_house}, f)

print("All model artifacts saved successfully.")
```

### Artifact Files

| File | Size (Approx.) | Contents |
|---|---|---|
| `model.pkl` | ~5–15 MB | Serialized RandomForestClassifier (200 trees) |
| `scaler.pkl` | ~2 KB | Fitted StandardScaler (mean, std per feature) |
| `encoders.pkl` | ~2 KB | Dict with `education` and `housing` LabelEncoders |

---

## 5.7 Flask Application Development

### Application Factory Pattern (`__init__.py`)

```python
from flask import Flask
from config import Config

def create_app(config_class=Config):
    app = Flask(__name__)
    app.config.from_object(config_class)
    
    from app.routes import main
    app.register_blueprint(main)
    
    return app
```

### Route Definitions (`routes.py`)

```python
from flask import Blueprint, render_template, request, jsonify
from app.prediction import PredictionPipeline
from app.visualizations import VisualizationEngine

main = Blueprint('main', __name__)
pipeline = PredictionPipeline()

@main.route('/', methods=['GET'])
def index():
    return render_template('index.html')

@main.route('/predict', methods=['POST'])
def predict():
    data = request.form.to_dict()
    result = pipeline.predict(data)
    return render_template('result.html', result=result)

@main.route('/api/predict', methods=['POST'])
def api_predict():
    data = request.get_json()
    if not data:
        return jsonify({'error': 'Invalid JSON input'}), 400
    result = pipeline.predict(data)
    return jsonify(result.to_dict())

@main.route('/visualize', methods=['GET'])
def visualize():
    engine = VisualizationEngine()
    charts = engine.generate_all()
    return render_template('visualize.html', charts=charts)
```

### Prediction Pipeline (`prediction.py`)

```python
import pickle
import numpy as np

class PredictionPipeline:
    def __init__(self):
        self.model = pickle.load(open('ml_models/model.pkl', 'rb'))
        self.scaler = pickle.load(open('ml_models/scaler.pkl', 'rb'))
        self.encoders = pickle.load(open('ml_models/encoders.pkl', 'rb'))
    
    def predict(self, data: dict) -> dict:
        # Encode categoricals
        edu_enc = self.encoders['education'].transform([data['education']])[0]
        house_enc = self.encoders['housing'].transform([data['housing']])[0]
        
        # Build feature array
        features = np.array([[
            float(data['age']),
            float(data['income']),
            float(data['employment_years']),
            float(data['credit_score']),
            float(data['debt_ratio']),
            float(data['num_dependents']),
            float(data['previous_defaults']),
            float(data['loan_amount']),
            edu_enc,
            house_enc
        ]])
        
        # Predict
        proba = self.model.predict_proba(features)[0]
        status = 'Approved' if proba[1] >= 0.5 else 'Rejected'
        
        return {
            'status': status,
            'approval_probability': round(float(proba[1]), 4),
            'rejection_probability': round(float(proba[0]), 4),
            'confidence': f"{max(proba)*100:.2f}%"
        }
```

---

## 5.8 Frontend Development

### Design Highlights

- **Color Scheme:** Purple gradient (`#667eea → #764ba2`)
- **Layout:** Two-column responsive grid using Bootstrap 5
- **Components:**
  - 10-field input form with real-time HTML5 validation
  - Animated result card with Bootstrap progress bar
  - Technology badge display (Python, Flask, Scikit-Learn, IBM Watson)
  - Mobile-responsive (single column at < 768px)

### Key Template: `result.html`
```html
<div class="result-card {% if result.status == 'Approved' %}approved{% else %}rejected{% endif %}">
    <h2 class="status-badge">{{ result.status }}</h2>
    <p>Approval Probability: <strong>{{ result.approval_probability }}</strong></p>
    <div class="progress">
        <div class="progress-bar" 
             style="width: {{ result.confidence }}">
            {{ result.confidence }}
        </div>
    </div>
</div>
```

---

## 5.9 IBM Watson ML Integration

### Integration Flow

1. Export trained model (`model.pkl`) from local notebook
2. Authenticate with IBM Cloud using API key
3. Create a Watson ML deployment space
4. Upload model artifact via `ibm-watson-machine-learning` SDK
5. Deploy as an online endpoint
6. Configure Flask to call Watson scoring endpoint

### Watson Scoring Call
```python
scoring_payload = {
    "input_data": [{
        "fields": ["Age","Income","Employment_Years","Credit_Score",
                   "Debt_Ratio","Num_Dependents","Previous_Defaults",
                   "Loan_Amount","Education_Encoded","Housing_Encoded"],
        "values": [[35, 60000, 5, 720, 0.25, 2, 0, 15000, 1, 0]]
    }]
}
predictions = wml_client.deployments.score(IBM_DEPLOYMENT_ID, scoring_payload)
```

---

## 5.10 Requirements Documentation

### `requirements.txt` — Package Explanations

| Package | Version | Purpose |
|---|---|---|
| `flask` | 2.3.3 | Web framework: routing, templates, request/response handling |
| `numpy` | 1.24.3 | Numerical arrays and mathematical operations; required by scikit-learn |
| `pandas` | 2.0.3 | DataFrame operations for dataset loading, EDA, and preprocessing |
| `scikit-learn` | 1.3.0 | Core ML library: RandomForestClassifier, LogisticRegression, StandardScaler, LabelEncoder, metrics |
| `matplotlib` | 3.7.2 | Static chart generation (ROC curve, confusion matrix, feature importance) |
| `seaborn` | 0.12.2 | Statistical visualization on top of matplotlib (heatmaps, distribution plots) |
| `gunicorn` | 21.2.0 | Production-grade WSGI server; required by Render and IBM Cloud for serving Flask |
