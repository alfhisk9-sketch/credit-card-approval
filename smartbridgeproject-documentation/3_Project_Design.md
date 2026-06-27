# Phase 3: Project Design

**Project:** AI-Based Credit Card Approval Prediction System
**Program:** SmartBridge Externship | AICTE | IBM SkillsBuild

---

## 3.1 System Architecture

The system follows a **three-tier web architecture** integrated with a **machine learning inference layer** and **cloud deployment**:

```
┌─────────────────────────────────────────────────────┐
│                  PRESENTATION TIER                  │
│    HTML5 · CSS3 · Bootstrap · JavaScript (ES6)      │
│         Input Form │ Result Card │ Dashboard        │
└──────────────────────┬──────────────────────────────┘
                       │ HTTP/HTTPS
┌──────────────────────▼──────────────────────────────┐
│                 APPLICATION TIER                    │
│              Flask 2.3.3 + Gunicorn                 │
│    Routes │ Validation │ Preprocessing │ API Layer  │
└──────────┬──────────────────────────┬───────────────┘
           │                          │
┌──────────▼──────────┐   ┌──────────▼───────────────┐
│    ML INFERENCE     │   │     DATA / STORAGE       │
│  Random Forest .pkl │   │  SQLite DB │ CSV Dataset │
│  Scaler.pkl         │   │  model.pkl │ scaler.pkl  │
│  Encoders.pkl       │   │  encoders.pkl            │
└──────────┬──────────┘   └──────────────────────────┘
           │ Optional
┌──────────▼──────────┐
│   IBM WATSON ML     │
│  Cloud Inference    │
│  Scoring Endpoint   │
└─────────────────────┘
```

---

## 3.2 Mermaid Architecture Diagram

```mermaid
graph TB
    subgraph Client["Client Layer"]
        A[User Browser]
    end

    subgraph AppLayer["Flask Application Layer (Render / IBM Cloud)"]
        B[Route Handler]
        C[Input Validator]
        D[Preprocessing Pipeline]
        E[Prediction Engine]
        F[Visualization Engine]
        G[REST API /api/predict]
    end

    subgraph MLLayer["ML Model Layer"]
        H[model.pkl - Random Forest]
        I[scaler.pkl - StandardScaler]
        J[encoders.pkl - LabelEncoders]
    end

    subgraph CloudLayer["Cloud Layer"]
        K[IBM Watson ML Endpoint]
    end

    subgraph DataLayer["Data Layer"]
        L[(SQLite DB)]
        M[credit_approval_dataset.csv]
    end

    A -->|HTTP POST /predict| B
    A -->|HTTP POST /api/predict| G
    A -->|HTTP GET /visualize| F
    B --> C
    C --> D
    D --> J
    J --> I
    I --> E
    E --> H
    H -->|Approval + Probability| B
    B -->|HTML Response| A
    G -->|JSON Response| A
    F -->|Chart Images Base64| A
    E -.->|Optional| K
    B --> L
    H -.->|Trained from| M
```

---

## 3.3 Data Flow Diagram (DFD)

### DFD Level 0 — Context Diagram

```mermaid
graph LR
    APPLICANT([Applicant]) -->|Application Data| SYSTEM[Credit Approval\nPrediction System]
    SYSTEM -->|Approval Decision + Probability| APPLICANT
    BANKOFFICER([Bank Officer]) -->|Admin Access| SYSTEM
    SYSTEM -->|Analytics Dashboard| BANKOFFICER
    IBMCLOUD([IBM Watson Cloud]) <-->|Model Inference| SYSTEM
```

### DFD Level 1 — System Processes

```mermaid
flowchart TD
    USER([User]) -->|Form Data| P1[1.0\nInput Processing\n& Validation]
    P1 -->|Validated Features| P2[2.0\nFeature\nPreprocessing]
    P2 -->|Encoded + Scaled Features| P3[3.0\nML Prediction\nEngine]
    P3 -->|Prediction Result| P4[4.0\nResult\nFormatting]
    P4 -->|HTML/JSON Response| USER
    P3 -->|Log Entry| DS1[(Prediction Log DB)]
    DS2[(Model Artifacts\n.pkl files)] -->|Load Model| P3
    DS3[(Training Dataset)] -->|EDA & Viz Data| P5[5.0\nVisualization\nEngine]
    P5 -->|Charts| USER
```

---

## 3.4 Use Case Diagram

```mermaid
graph LR
    subgraph Actors
        UA([Applicant\nUser])
        BA([Bank\nOfficer])
        SYS([IBM Watson\nCloud])
    end

    subgraph System["Credit Approval System"]
        UC1[Submit Application Form]
        UC2[View Prediction Result]
        UC3[View Analytics Dashboard]
        UC4[Call REST API]
        UC5[Access Admin Panel]
        UC6[View Model Metrics]
        UC7[Export Model to Watson]
        UC8[Score via Watson Endpoint]
    end

    UA --> UC1
    UA --> UC2
    UA --> UC4
    BA --> UC5
    BA --> UC3
    BA --> UC6
    BA --> UC7
    SYS --> UC8
    UC1 -.includes.-> UC2
    UC7 -.includes.-> UC8
```

---

## 3.5 Sequence Diagram

```mermaid
sequenceDiagram
    actor User
    participant Browser
    participant Flask
    participant Validator
    participant Preprocessor
    participant RandomForest
    participant DB

    User->>Browser: Fill 10-field form and submit
    Browser->>Flask: POST /predict (form data)
    Flask->>Validator: Validate all field ranges
    alt Invalid Input
        Validator-->>Flask: Validation Error
        Flask-->>Browser: 400 Bad Request + Error Message
        Browser-->>User: Display inline error
    else Valid Input
        Validator-->>Flask: Validated data dict
        Flask->>Preprocessor: Label Encode (Education, Housing)
        Preprocessor->>Preprocessor: StandardScaler.transform()
        Preprocessor-->>Flask: Scaled feature array
        Flask->>RandomForest: model.predict_proba(features)
        RandomForest-->>Flask: [P(Reject), P(Approve)]
        Flask->>DB: Log(applicant_data, result, timestamp)
        Flask-->>Browser: Render result.html (status + probability)
        Browser-->>User: Display Result Card with confidence bar
    end
```

---

## 3.6 Activity Diagram

```mermaid
flowchart TD
    Start([Start]) --> A[User Opens Application]
    A --> B[Display Input Form]
    B --> C[User Fills 10 Fields]
    C --> D{Client-Side\nValidation Passes?}
    D -- No --> E[Show Inline Error Messages]
    E --> C
    D -- Yes --> F[Submit POST Request]
    F --> G{Server-Side\nValidation Passes?}
    G -- No --> H[Return 400 Error Response]
    H --> B
    G -- Yes --> I[Label Encode Categorical Features]
    I --> J[Apply StandardScaler]
    J --> K[Run Random Forest Predict_proba]
    K --> L{Approval Probability\n> 0.5?}
    L -- Yes --> M[Status = APPROVED]
    L -- No --> N[Status = REJECTED]
    M --> O[Log Result to DB]
    N --> O
    O --> P[Render Result Card]
    P --> Q{User Wants\nVisualization?}
    Q -- Yes --> R[Generate Charts via Matplotlib/Seaborn]
    R --> S[Display Analytics Dashboard]
    Q -- No --> End([End])
    S --> End
```

---

## 3.7 Component Diagram

```mermaid
graph TB
    subgraph Frontend["Frontend Components"]
        F1[index.html\nInput Form]
        F2[result.html\nResult Card]
        F3[visualize.html\nDashboard]
        F4[style.css\nStyling]
        F5[app.js\nValidation & Async]
    end

    subgraph Backend["Backend Components"]
        B1[run.py\nEntry Point]
        B2[config.py\nConfiguration]
        B3[routes.py\nURL Routing]
        B4[prediction.py\nML Pipeline]
        B5[visualizations.py\nChart Generation]
        B6[__init__.py\nApp Factory]
    end

    subgraph MLArtifacts["ML Artifacts"]
        M1[model.pkl\nRandom Forest]
        M2[scaler.pkl\nStandardScaler]
        M3[encoders.pkl\nLabelEncoders]
    end

    subgraph Data["Data Layer"]
        D1[SQLite DB\napp.db]
        D2[credit_approval_dataset.csv]
    end

    F1 --> B3
    F2 --> B3
    F3 --> B3
    B1 --> B6
    B6 --> B3
    B6 --> B2
    B3 --> B4
    B3 --> B5
    B4 --> M1
    B4 --> M2
    B4 --> M3
    B4 --> D1
    B5 --> D2
```

---

## 3.8 Deployment Diagram

```mermaid
graph TB
    subgraph Internet["Internet"]
        USER[User Browser]
    end

    subgraph Render["Render Cloud (Production)"]
        WS[Web Service\nGunicorn WSGI]
        APP[Flask Application\nPython 3.9]
        DB[(SQLite\napp.db)]
        PKL[Model Artifacts\n.pkl files]
    end

    subgraph IBM["IBM Cloud (Alternative / Enterprise)"]
        WML[Watson Machine Learning\nDeployment Space]
        CF[Cloud Foundry\nApp Runtime]
    end

    subgraph GitHub["GitHub"]
        REPO[Repository\nmain branch]
    end

    USER <-->|HTTPS| WS
    WS --> APP
    APP --> DB
    APP --> PKL
    REPO -->|CD Auto Deploy| WS
    APP -.->|Optional WML Scoring| WML
    REPO -.->|Alt Deploy| CF
    CF -.-> WML
```

---

## 3.9 Class Diagram

```mermaid
classDiagram
    class FlaskApp {
        +config: Config
        +db: SQLite
        +run()
        +register_routes()
    }

    class PredictionPipeline {
        -model: RandomForestClassifier
        -scaler: StandardScaler
        -encoders: dict
        +load_artifacts()
        +encode(data: dict) dict
        +scale(data: array) array
        +predict(data: dict) PredictionResult
    }

    class PredictionResult {
        +status: str
        +approval_probability: float
        +rejection_probability: float
        +confidence_percentage: str
    }

    class InputValidator {
        +validate_age(age: int) bool
        +validate_income(income: float) bool
        +validate_credit_score(score: int) bool
        +validate_debt_ratio(ratio: float) bool
        +validate_all(data: dict) tuple
    }

    class VisualizationEngine {
        -dataset: DataFrame
        +plot_distribution() str
        +plot_feature_importance(model) str
        +plot_roc_curve(model, X_test, y_test) str
        +plot_confusion_matrix(y_test, y_pred) str
        +plot_correlation_heatmap() str
        +to_base64(fig) str
    }

    class PredictionLog {
        +id: int
        +timestamp: datetime
        +age: int
        +income: float
        +credit_score: int
        +result: str
        +probability: float
        +save()
    }

    class RandomForestModel {
        +n_estimators: int
        +max_depth: int
        +random_state: int
        +fit(X, y)
        +predict(X) array
        +predict_proba(X) array
        +feature_importances_: array
    }

    FlaskApp --> PredictionPipeline
    FlaskApp --> VisualizationEngine
    FlaskApp --> InputValidator
    PredictionPipeline --> RandomForestModel
    PredictionPipeline --> PredictionResult
    PredictionPipeline --> PredictionLog
```

---

## 3.10 ER Diagram

```mermaid
erDiagram
    PREDICTION_LOG {
        int id PK
        datetime timestamp
        int age
        float annual_income
        int employment_years
        int credit_score
        float debt_ratio
        int num_dependents
        varchar education
        varchar housing_status
        int previous_defaults
        float loan_amount
        varchar prediction_result
        float approval_probability
        float rejection_probability
    }

    MODEL_METADATA {
        int id PK
        varchar model_name
        varchar algorithm
        float accuracy
        float auc_roc
        datetime trained_at
        varchar artifact_path
    }

    USER_SESSION {
        varchar session_id PK
        datetime created_at
        int prediction_count
    }

    USER_SESSION ||--o{ PREDICTION_LOG : "generates"
    MODEL_METADATA ||--o{ PREDICTION_LOG : "produces"
```

---

## 3.11 Database Design

### Table: prediction_log

| Column | Type | Constraints | Description |
|---|---|---|---|
| id | INTEGER | PRIMARY KEY, AUTOINCREMENT | Unique record identifier |
| timestamp | DATETIME | NOT NULL, DEFAULT NOW | When prediction was made |
| age | INTEGER | NOT NULL, CHECK(18–100) | Applicant age |
| annual_income | REAL | NOT NULL, CHECK(≥0) | Annual income in INR |
| employment_years | INTEGER | NOT NULL, CHECK(0–50) | Years employed |
| credit_score | INTEGER | NOT NULL, CHECK(300–850) | CIBIL credit score |
| debt_ratio | REAL | NOT NULL, CHECK(0.0–1.0) | Debt-to-income ratio |
| num_dependents | INTEGER | NOT NULL, CHECK(0–10) | Number of dependents |
| education | VARCHAR(20) | NOT NULL | Education level |
| housing_status | VARCHAR(20) | NOT NULL | Housing type |
| previous_defaults | INTEGER | NOT NULL, CHECK(0 OR 1) | Default history flag |
| loan_amount | REAL | NOT NULL, CHECK(≥0) | Requested loan amount |
| prediction_result | VARCHAR(10) | NOT NULL | "Approved" or "Rejected" |
| approval_probability | REAL | NOT NULL | P(Approval) from model |

---

## 3.12 UI/UX Design Specification

### Color Palette

| Element | Color | Hex Code |
|---|---|---|
| Primary Gradient Start | Purple | `#667eea` |
| Primary Gradient End | Deep Purple | `#764ba2` |
| Approved Status | Green | `#28a745` |
| Rejected Status | Red | `#dc3545` |
| Card Background | White | `#ffffff` |
| Body Background | Light Grey | `#f8f9fa` |
| Text Primary | Dark | `#2c3e50` |

### Responsive Breakpoints

| Breakpoint | Layout |
|---|---|
| ≥ 768px | Two-column (Form left, Result right) |
| < 768px | Single-column stack |

### Form Field Mapping

| Field | HTML Type | Validation |
|---|---|---|
| Age | `number` | min=18, max=100 |
| Annual Income | `number` | min=0, step=1000 |
| Employment Years | `number` | min=0, max=50 |
| Credit Score | `number` | min=300, max=850 |
| Debt Ratio | `number` | min=0.0, max=1.0, step=0.01 |
| Num Dependents | `number` | min=0, max=10 |
| Education | `select` | Dropdown (4 options) |
| Housing Status | `select` | Dropdown (4 options) |
| Previous Defaults | `select` | Yes / No |
| Loan Amount | `number` | min=0, step=500 |
