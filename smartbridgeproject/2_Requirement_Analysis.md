# Phase 2: Requirement Analysis

**Project:** AI-Based Credit Card Approval Prediction System
**Program:** SmartBridge Externship | AICTE | IBM SkillsBuild

---

## 2.1 Functional Requirements

### FR-01: User Input Module

| ID | Requirement | Priority |
|---|---|---|
| FR-01.1 | System shall accept applicant Age (integer, 18–100) | Must Have |
| FR-01.2 | System shall accept Annual Income (numeric, ≥ 0) | Must Have |
| FR-01.3 | System shall accept Employment Years (0–50) | Must Have |
| FR-01.4 | System shall accept Credit Score (300–850) | Must Have |
| FR-01.5 | System shall accept Debt Ratio (0.0–1.0) | Must Have |
| FR-01.6 | System shall accept Number of Dependents (0–10) | Must Have |
| FR-01.7 | System shall accept Education Level (dropdown: High School / Bachelor / Master / PhD) | Must Have |
| FR-01.8 | System shall accept Housing Status (dropdown: Rent / Own / Mortgage / Other) | Must Have |
| FR-01.9 | System shall accept Previous Defaults (binary: Yes / No) | Must Have |
| FR-01.10 | System shall accept Loan Amount Requested (numeric, ≥ 0) | Must Have |

### FR-02: Prediction Engine

| ID | Requirement | Priority |
|---|---|---|
| FR-02.1 | System shall classify applicant as Approved or Rejected | Must Have |
| FR-02.2 | System shall output approval probability (0.0–1.0) | Must Have |
| FR-02.3 | System shall display confidence percentage in a progress bar | Should Have |
| FR-02.4 | System shall use Random Forest as the primary classifier | Must Have |
| FR-02.5 | System shall use Logistic Regression as a baseline comparator | Should Have |
| FR-02.6 | System shall complete a prediction in < 2 seconds | Must Have |

### FR-03: Validation Module

| ID | Requirement | Priority |
|---|---|---|
| FR-03.1 | System shall validate all numeric fields for range constraints | Must Have |
| FR-03.2 | System shall reject form submission if any required field is empty | Must Have |
| FR-03.3 | System shall display descriptive error messages for invalid inputs | Must Have |
| FR-03.4 | System shall sanitize all inputs to prevent XSS | Must Have |

### FR-04: Visualization Module

| ID | Requirement | Priority |
|---|---|---|
| FR-04.1 | System shall display approval/rejection distribution as a pie chart | Should Have |
| FR-04.2 | System shall display feature importance as a horizontal bar chart | Should Have |
| FR-04.3 | System shall display credit score vs approval as a box plot | Could Have |
| FR-04.4 | System shall display a correlation heatmap of all features | Could Have |
| FR-04.5 | System shall display ROC curve with AUC annotation | Should Have |
| FR-04.6 | System shall display a confusion matrix heatmap | Should Have |

### FR-05: REST API Module

| ID | Requirement | Priority |
|---|---|---|
| FR-05.1 | System shall expose POST `/api/predict` accepting JSON input | Must Have |
| FR-05.2 | System shall return JSON response with status, probabilities | Must Have |
| FR-05.3 | System shall return HTTP 400 for malformed or invalid input | Must Have |
| FR-05.4 | System shall return HTTP 500 with error message for server failures | Should Have |

### FR-06: IBM Watson Integration

| ID | Requirement | Priority |
|---|---|---|
| FR-06.1 | System shall support model deployment on IBM Watson ML | Must Have |
| FR-06.2 | System shall support inference via Watson scoring endpoint | Must Have |
| FR-06.3 | System shall authenticate using IBM Cloud API key | Must Have |

---

## 2.2 Non-Functional Requirements

| ID | Category | Requirement | Target |
|---|---|---|---|
| NFR-01 | Performance | Prediction response time | < 2 seconds end-to-end |
| NFR-02 | Performance | Page load time | < 3 seconds on 4G |
| NFR-03 | Accuracy | Model prediction accuracy | ≥ 85% on test set |
| NFR-04 | Accuracy | AUC-ROC score | ≥ 0.90 |
| NFR-05 | Scalability | Concurrent users supported | ≥ 100 simultaneous |
| NFR-06 | Availability | System uptime | ≥ 99% (Render SLA) |
| NFR-07 | Security | Input sanitization | All user inputs sanitized |
| NFR-08 | Security | Transport encryption | HTTPS enforced |
| NFR-09 | Usability | Mobile responsiveness | Layout adapts ≤ 768px viewport |
| NFR-10 | Maintainability | Code documentation | All functions docstring-documented |
| NFR-11 | Portability | Model artifacts | Portable via `.pkl` files |
| NFR-12 | Reliability | Error handling | Graceful degradation with error pages |

---

## 2.3 Requirement Traceability Matrix (RTM)

| Requirement ID | Module | Test Case ID | Status |
|---|---|---|---|
| FR-01.1 – FR-01.10 | Input Form | TC-01.1 – TC-01.10 | ✅ Implemented & Tested |
| FR-02.1 | Prediction Engine | TC-02.1 | ✅ Implemented & Tested |
| FR-02.2 | Prediction Engine | TC-02.2 | ✅ Implemented & Tested |
| FR-02.6 | Prediction Engine | TC-02.6 | ✅ Tested (0.3s) |
| FR-03.1 – FR-03.4 | Validation | TC-03.1 – TC-03.4 | ✅ Implemented & Tested |
| FR-04.1 – FR-04.6 | Visualization | TC-04.1 – TC-04.6 | ✅ Implemented & Tested |
| FR-05.1 – FR-05.4 | REST API | TC-05.1 – TC-05.4 | ✅ Implemented & Tested |
| FR-06.1 – FR-06.3 | IBM Watson | TC-06.1 – TC-06.3 | ✅ Configured |
| NFR-01 – NFR-12 | System-wide | PT-01 – PT-12 | ✅ Verified |

---

## 2.4 Feasibility Study

### Technical Feasibility

| Factor | Assessment |
|---|---|
| ML Algorithm (Random Forest) | ✅ Mature, well-supported in scikit-learn |
| Flask Web Framework | ✅ Lightweight, easy to deploy |
| IBM Watson Integration | ✅ Standard API, well-documented |
| Dataset Availability | ✅ Synthetic dataset generated with realistic distributions |
| Team Skill Level | ✅ All required skills present across 5 team members |

**Verdict: Technically Feasible**

### Economic Feasibility

| Cost Item | Estimated Cost |
|---|---|
| Cloud Hosting (Render Free Tier) | ₹0 |
| IBM Watson (Lite Plan) | ₹0 |
| Python / Flask / Libraries | ₹0 (Open Source) |
| Development Time (5 members × 8 weeks) | Time investment only |
| Domain Name (optional) | ₹500–1000/year |

**Verdict: Economically Feasible — Zero monetary cost for development and deployment**

### Operational Feasibility

- All team members have adequate Python and ML knowledge
- Flask is straightforward to maintain and update
- IBM Watson and Render provide managed infrastructure
- GitHub enables collaborative version-controlled development

**Verdict: Operationally Feasible**

---

## 2.5 Risk Analysis

| Risk ID | Risk Description | Probability | Impact | Mitigation Strategy |
|---|---|---|---|---|
| R-01 | Dataset imbalance leading to biased model | Medium | High | Ensure balanced class distribution; use stratified split |
| R-02 | Model overfitting on training data | Medium | High | Apply cross-validation, regularization, max_depth limit |
| R-03 | IBM Watson deployment failure | Low | High | Test locally with pickle model first; fallback to local inference |
| R-04 | Team member unavailability | Medium | Medium | Thorough documentation; async collaboration via GitHub |
| R-05 | Render free-tier cold start latency | High | Low | Warm-up endpoint; mention in documentation |
| R-06 | Security vulnerabilities in form inputs | Medium | High | Implement server-side validation; Flask auto-escaping |
| R-07 | Flask app crashes under high load | Low | Medium | Use Gunicorn with multiple workers |
| R-08 | Model accuracy below 85% | Low | High | Try multiple algorithms; hyperparameter tuning |

---

## 2.6 Software Requirements

| Software | Version | Purpose |
|---|---|---|
| Python | 3.9+ | Core language |
| Flask | 2.3.3 | Web framework |
| Gunicorn | 21.2.0 | WSGI production server |
| Scikit-Learn | 1.3.0 | ML algorithms and preprocessing |
| Pandas | 2.0.3 | Data manipulation |
| NumPy | 1.24.3 | Numerical operations |
| Matplotlib | 3.7.2 | Chart generation |
| Seaborn | 0.12.2 | Statistical visualization |
| Jupyter Notebook | Any | Model training environment |
| Git | 2.x+ | Version control |
| IBM WML SDK | Latest | Watson ML integration |

---

## 2.7 Hardware Requirements

### Development Environment

| Component | Minimum | Recommended |
|---|---|---|
| Processor | Intel Core i5 | Intel Core i7 / Ryzen 7 |
| RAM | 8 GB | 16 GB |
| Storage | 10 GB free | 50 GB SSD |
| OS | Windows 10 / Ubuntu 20.04 | Windows 11 / Ubuntu 22.04 |
| Internet | 10 Mbps | 50+ Mbps |

### Production Environment (Render / IBM Cloud)

| Component | Specification |
|---|---|
| Instance Type | Render Free (512 MB RAM, 0.1 CPU) |
| Storage | 1 GB (model + app) |
| Network | HTTPS, public internet |
| OS | Linux (Ubuntu) |
| Python Runtime | 3.9.x |

---

## 2.8 Dataset Requirements

| Criterion | Requirement |
|---|---|
| Minimum Records | 3,000+ labeled rows |
| Features | 10 input + 1 target variable |
| Target Variable | Binary: Approved (1) / Rejected (0) |
| Class Balance | Approximately 50% each class |
| Data Quality | No null values after preprocessing |
| Feature Types | Mix of numeric and categorical |
| Format | CSV (UTF-8 encoded) |
