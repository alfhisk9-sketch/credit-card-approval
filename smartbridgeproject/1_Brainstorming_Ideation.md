# Phase 1: Brainstorming & Ideation

**Project:** AI-Based Credit Card Approval Prediction System
**Program:** SmartBridge Externship | AICTE | IBM SkillsBuild
**Date:** 2025

---

## 1.1 Problem Identification

### Industry Context

The global credit card market processes millions of applications every year. In India alone, as of 2024, over 100 million active credit cards are in circulation, with new applications growing at 15–20% annually. Financial institutions face a fundamental operational challenge: how to assess creditworthiness quickly, accurately, and without bias.

### Core Problem

Traditional credit card approval systems rely on:
- **Manual review** by credit analysts (slow, expensive, inconsistent)
- **Rule-based scoring** using rigid threshold criteria (lacks nuance)
- **Credit bureau checks** alone (incomplete view of applicant risk)

These systems suffer from:

| Problem | Impact |
|---|---|
| Processing delay (3–7 business days) | Poor customer experience, lost business |
| Human bias and inconsistency | Legal risk, reputational damage |
| High operational cost | ₹500–2000 per manual review |
| Limited feature utilization | Suboptimal risk assessment |
| No real-time decisioning | Inability to scale |

### Problem Statement (Formal)

> *Financial institutions require an automated, intelligent system that can accurately predict credit card approval decisions in real time by analyzing applicant demographic and financial data — reducing processing time from days to seconds while maintaining high prediction accuracy, consistency, and fairness.*

---

## 1.2 Idea Generation & Prioritization

### Brainstorming Session Outcomes

The team conducted a structured brainstorming session using the "How Might We" (HMW) framework:

| HMW Question | Generated Ideas |
|---|---|
| How might we automate approval decisions? | Rule engine, ML classifier, scoring API, neural network |
| How might we make the system explainable? | SHAP values, feature importance charts, confidence scores |
| How might we deploy this for bank use? | REST API, IBM Watson, web portal, mobile app |
| How might we validate the predictions? | Cross-validation, confusion matrix, ROC-AUC curve |
| How might we handle unfair bias? | Fairness audit, balanced dataset, demographic parity |

### Idea Prioritization Matrix

Ideas were evaluated on **Feasibility × Impact**:

| Idea | Feasibility (1–5) | Impact (1–5) | Score | Decision |
|---|---|---|---|---|
| Random Forest Classifier Web App | 5 | 5 | 25 | ✅ Selected (Primary) |
| Logistic Regression Baseline | 5 | 3 | 15 | ✅ Selected (Baseline) |
| Neural Network (Deep Learning) | 2 | 5 | 10 | ❌ Too complex for timeline |
| Mobile App | 2 | 4 | 8 | ❌ Scope deferred |
| Blockchain Audit Log | 1 | 3 | 3 | ❌ Out of scope |
| SHAP Explainability | 3 | 4 | 12 | 🔄 Future Enhancement |

**Selected Solution:** Machine Learning-powered Flask web application with REST API, data visualization, and IBM Watson cloud deployment.

---

## 1.3 Empathy Map

### Target Users

**Primary User:** Credit Officer / Risk Analyst at a bank
**Secondary User:** Applicant checking approval likelihood
**Tertiary User:** Bank IT Administrator managing the system

### Empathy Map: Credit Officer

| Quadrant | Details |
|---|---|
| **THINKS** | "I need to process 200 applications today. The rules keep changing. I hope I'm not making biased decisions." |
| **FEELS** | Overwhelmed by volume. Anxious about compliance. Frustrated by lack of data tools. |
| **SAYS** | "This takes too long." / "We need a smarter system." / "I can't manually check everything." |
| **DOES** | Reviews applications one by one. Uses spreadsheets. Consults credit bureau reports. Escalates borderline cases. |
| **PAIN POINTS** | Time pressure, inconsistency across reviewers, lack of explainability, fear of regulatory audit |
| **GAINS SOUGHT** | Speed, accuracy, consistency, explainability, compliance confidence |

### Empathy Map: Applicant

| Quadrant | Details |
|---|---|
| **THINKS** | "Will I be approved? How long will it take? What are my chances?" |
| **FEELS** | Anxious, uncertain, impatient |
| **SAYS** | "I need a quick answer." / "I don't understand why I was rejected." |
| **DOES** | Submits application, waits, calls customer service |
| **PAIN POINTS** | Waiting days for a decision, no transparency, no guidance on improving chances |
| **GAINS SOUGHT** | Instant decision, clear reasoning, confidence score |

---

## 1.4 Stakeholder Analysis

| Stakeholder | Role | Interest | Influence | Engagement Strategy |
|---|---|---|---|---|
| Bank / NBFC Management | Decision maker | ROI, risk reduction, compliance | High | Present ROI analysis and accuracy metrics |
| Credit Risk Officers | Primary users | Speed, accuracy, usability | High | Involve in requirements gathering and UAT |
| IT / DevOps Team | System integrators | API stability, security, scalability | Medium | Provide REST API docs and deployment guide |
| Credit Card Applicants | End beneficiaries | Fast, fair decisions | Low | Design transparent UI with confidence scores |
| Regulators (RBI) | Compliance authority | Fairness, explainability, data privacy | High | Implement audit logging and bias checks |
| SmartBridge / AICTE | Program evaluators | Project quality and documentation | Medium | Deliver complete professional documentation |
| IBM (Watson) | Cloud provider | API usage, platform adoption | Low | Follow Watson integration best practices |

---

## 1.5 Expected Outcomes

### Quantitative Targets

| Metric | Target | Actual (Achieved) |
|---|---|---|
| Model Accuracy | ≥ 85% | 88.83% ✅ |
| AUC-ROC Score | ≥ 0.90 | 0.94 ✅ |
| Prediction Latency | < 2 seconds | ~0.3 seconds ✅ |
| Test Case Pass Rate | 100% | 100% ✅ |
| Page Load Time | < 3 seconds | ~1.2 seconds ✅ |

### Qualitative Outcomes

- A fully functional, publicly accessible web application
- A documented, reproducible ML training pipeline
- A professional REST API with JSON I/O
- IBM Watson cloud integration for enterprise scalability
- Complete SmartBridge project documentation set (8 phases)
- GitHub repository with structured codebase
- Submission-ready engineering report

---

## 1.6 Innovation Canvas

| Dimension | Description |
|---|---|
| **Problem** | Manual, slow, biased credit card approval process |
| **Solution** | ML-powered real-time prediction web application |
| **Key Activities** | Data preprocessing, model training, Flask development, deployment |
| **Key Resources** | Dataset, Python stack, IBM Watson, GitHub, Render |
| **Value Proposition** | Instant decisions, 88.83% accuracy, explainable outputs, REST API |
| **Target Segment** | Banks, NBFCs, FinTech startups |
| **Channels** | Web browser, REST API, IBM Watson endpoint |
| **Cost Structure** | Free-tier cloud hosting, open-source tools only |
| **Revenue Potential** | SaaS licensing, API call pricing, enterprise integration |

---

## 1.7 Technology Justification

| Choice | Alternatives Considered | Reason for Selection |
|---|---|---|
| Random Forest | SVM, XGBoost, Neural Network | Best accuracy/interpretability trade-off; handles non-linear relationships; built-in feature importance |
| Flask | Django, FastAPI | Lightweight, minimal overhead, ideal for ML model serving |
| IBM Watson | AWS SageMaker, Azure ML | Program requirement; enterprise-grade ML serving |
| Render | Heroku, Railway | Free tier available; simple GitHub-based CI/CD |
| SQLite | PostgreSQL, MySQL | Sufficient for prototype; zero-config; portable |
| Bootstrap | Tailwind, Material UI | Rapid responsive UI development with CDN delivery |
