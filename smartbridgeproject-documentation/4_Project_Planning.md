# Phase 4: Project Planning

**Project:** AI-Based Credit Card Approval Prediction System
**Program:** SmartBridge Externship | AICTE | IBM SkillsBuild
**Duration:** 8 Weeks

---

## 4.1 Project Overview

| Parameter | Details |
|---|---|
| **Project Title** | AI-Based Credit Card Approval Prediction System |
| **Project Type** | SmartBridge Externship — Machine Learning Web Application |
| **Total Duration** | 8 Weeks |
| **Team Size** | 5 Members |
| **Methodology** | Agile with 4 Sprints |
| **Version Control** | Git + GitHub |
| **Deployment Targets** | IBM Watson ML + Render |

---

## 4.2 Team Roles & Responsibilities

| Member | Role | Primary Responsibilities |
|---|---|---|
| **SK Alfhi** | Application Builder & Frontend Developer | Flask app development, UI design, ML integration, IBM Watson, GitHub management, Render deployment, documentation coordination |
| **SK Rabbani** | Machine Learning Engineer | Dataset cleaning, feature engineering, model training & tuning, evaluation, model saving |
| **Bheemuni Pujitha** | Team Lead · Data Analyst · Visualization Engineer | Team coordination, requirement analysis, EDA, data visualization, reporting, documentation review |
| **Darla Krishna** | Data Collection Specialist | Dataset collection, data verification, missing value analysis, dataset preparation, data documentation |
| **Modugumudi TwineMallikadevi** | Testing & QA Engineer | Functional, integration, UI testing, bug reporting, validation testing, documentation verification |

---

## 4.3 Sprint Plan (Agile)

### Sprint 1 — Foundation (Weeks 1–2)

| Task | Owner | Status |
|---|---|---|
| Project kickoff and team role assignment | Bheemuni Pujitha | ✅ Done |
| Problem identification and brainstorming | All Members | ✅ Done |
| Requirement analysis and documentation | SK Alfhi | ✅ Done |
| Dataset collection and initial review | Darla Krishna | ✅ Done |
| GitHub repository creation and structure | SK Alfhi | ✅ Done |
| System architecture design | SK Alfhi | ✅ Done |
| UI wireframe design | SK Alfhi | ✅ Done |

### Sprint 2 — Data & Model (Weeks 3–4)

| Task | Owner | Status |
|---|---|---|
| Dataset cleaning and preprocessing | Darla Krishna, SK Rabbani | ✅ Done |
| Exploratory Data Analysis (EDA) | Bheemuni Pujitha | ✅ Done |
| Feature engineering | SK Rabbani | ✅ Done |
| Random Forest model training | SK Rabbani | ✅ Done |
| Logistic Regression baseline | SK Rabbani | ✅ Done |
| Hyperparameter tuning | SK Rabbani | ✅ Done |
| Model evaluation and metrics | SK Rabbani, Bheemuni Pujitha | ✅ Done |
| Model artifact export (.pkl) | SK Rabbani | ✅ Done |

### Sprint 3 — Development (Weeks 5–6)

| Task | Owner | Status |
|---|---|---|
| Flask application skeleton | SK Alfhi | ✅ Done |
| HTML/CSS/Bootstrap frontend | SK Alfhi | ✅ Done |
| Prediction pipeline integration | SK Alfhi | ✅ Done |
| REST API endpoint | SK Alfhi | ✅ Done |
| Visualization engine | Bheemuni Pujitha | ✅ Done |
| IBM Watson integration | SK Alfhi | ✅ Done |
| Unit testing | Modugumudi TwineMallikadevi | ✅ Done |
| Integration testing | Modugumudi TwineMallikadevi | ✅ Done |

### Sprint 4 — Deployment & Documentation (Weeks 7–8)

| Task | Owner | Status |
|---|---|---|
| Render deployment | SK Alfhi | ✅ Done |
| Performance testing | Modugumudi TwineMallikadevi | ✅ Done |
| Security testing | Modugumudi TwineMallikadevi | ✅ Done |
| README.md creation | SK Alfhi | ✅ Done |
| SmartBridge documentation (all 8 phases) | All Members | ✅ Done |
| Engineering project report | SK Alfhi, Bheemuni Pujitha | ✅ Done |
| Demo preparation and viva Q&A | All Members | ✅ Done |
| Final submission | Bheemuni Pujitha | ✅ Done |

---

## 4.4 Project Milestones

| Milestone | Target Week | Deliverable | Status |
|---|---|---|---|
| M1: Project Kickoff | Week 1 | Brainstorming doc, team roles assigned | ✅ Completed |
| M2: Requirements Finalized | Week 1 | Requirement Analysis document | ✅ Completed |
| M3: Architecture & Design | Week 2 | Design diagrams, UI wireframes | ✅ Completed |
| M4: Dataset Ready | Week 3 | Cleaned CSV, EDA report | ✅ Completed |
| M5: Model Trained | Week 4 | model.pkl with ≥85% accuracy | ✅ Completed (88.83%) |
| M6: App Built | Week 5 | Functional Flask application | ✅ Completed |
| M7: All Testing Passed | Week 6 | 15/15 test cases passed | ✅ Completed |
| M8: Deployed Live | Week 7 | Render + IBM Watson live | ✅ Completed |
| M9: Documentation Complete | Week 8 | Full SmartBridge package | ✅ Completed |
| M10: Final Submission | Week 8 | GitHub repo + report submitted | ✅ Completed |

---

## 4.5 Gantt Chart

```
WEEK →         W1    W2    W3    W4    W5    W6    W7    W8
─────────────────────────────────────────────────────────────
Brainstorming  ████
Requirements   ████
Design              ████
Dataset Prep        ████  ████
EDA & Viz                 ████
Model Training              ████
Model Evaluation            ████
Flask Backend                     ████
Frontend UI                       ████
IBM Integration                   ████
Unit Testing                            ████
Integration Test                        ████
Render Deploy                                 ████
Documentation              ████  ████  ████  ████  ████
Demo Prep                                           ████
Final Submit                                        ████
─────────────────────────────────────────────────────────────
SPRINT:        ──S1──────── ──S2──────── ──S3──────── ──S4──
```

---

## 4.6 Resource Allocation

| Resource | Allocated To | Hours/Week (Est.) |
|---|---|---|
| SK Alfhi | Flask dev, frontend, deployment, IBM Watson | 15–20 hrs |
| SK Rabbani | ML pipeline, model training, evaluation | 15–20 hrs |
| Bheemuni Pujitha | EDA, visualization, team coordination, docs | 12–15 hrs |
| Darla Krishna | Dataset prep, cleaning, documentation | 10–12 hrs |
| Modugumudi TwineMallikadevi | Testing, bug reports, validation | 10–12 hrs |

---

## 4.7 Risk Mitigation Plan

| Risk | Probability | Impact | Mitigation |
|---|---|---|---|
| Dataset imbalance | Medium | High | Generate balanced synthetic data; verify class distribution before training |
| Model accuracy < 85% | Low | High | Try multiple algorithms; tune hyperparameters; ensemble methods |
| IBM Watson API failure | Low | High | Implement local pickle-based fallback; test Watson locally first |
| Render cold start > 30s | High | Low | Document warm-up behavior; add health check endpoint |
| Team member absence | Medium | Medium | Document all code; use async GitHub workflow; pair programming |
| Security vulnerability | Low | High | Server-side validation; Flask Jinja2 auto-escaping; HTTPS via Render |
| Scope creep | Medium | Medium | Freeze scope after Sprint 1; defer extras to "Future Enhancements" |

---

## 4.8 Communication Plan

| Activity | Frequency | Channel | Participants |
|---|---|---|---|
| Sprint Planning | Weekly | WhatsApp / Meet | All Members |
| Progress Updates | Daily | WhatsApp Group | All Members |
| Code Review | Per PR | GitHub Pull Requests | SK Alfhi, SK Rabbani |
| Demo Rehearsal | Sprint end | Google Meet | All Members |
| Documentation Review | Sprint 4 | Shared Drive | All Members |

---

## 4.9 Definition of Done

A task is considered **Done** when:
1. Code is committed to GitHub with a descriptive commit message
2. Feature passes all related test cases
3. Documentation is updated to reflect changes
4. Team lead (Bheemuni Pujitha) has reviewed and approved
5. No critical bugs are open against the task
