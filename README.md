# James Koero

**Machine Learning Engineer | MLOps | Geospatial and Applied ML**

Kisumu, Kenya (EAT, UTC+3) | Open to remote roles | Async-friendly for EU and US teams

[LinkedIn](https://www.linkedin.com/in/jameskoero) | [ORCID](https://orcid.org/0009-0001-8314-2682) | [Zenodo release](https://doi.org/10.5281/zenodo.23919053) | jmskoero@gmail.com

---

## About

I build machine learning systems, then try to break them. In 2026 I audited my own flood model, found that its headline metric was circular, retracted it, and rebuilt the whole system from real satellite data under strict leakage control. The rebuild is public, released as v2.0.0, and every number below can be re-derived from files in the repository.

I came to ML from physics and geophysics: B.Sc. Physics and Mathematics (Moi University), a geophysics attachment at KenGen Olkaria, then seven years in Kenyan insurance and investment distribution. Everything here was built on an Android phone with Termux and Google Colab, over mobile data.

---

## Flagship: Nyando Flood AI V2

An open-source system that ranks flood susceptibility across five wards of the Nyando basin in Kenya.

**Links:** [Live dashboard](https://nyando-flood-ai.vercel.app/) | [Source code](https://github.com/jameskoero/nyando-flood-ai) | [v2.0.0 on Zenodo](https://doi.org/10.5281/zenodo.23919053)

| What | Result |
|---|---|
| Data | 4,420 samples over 35 Sentinel-1 scene dates (Copernicus GFM labels, Google Earth Engine). No synthetic data. |
| Sealed test | 27 held-out flood events, scored once under rules fixed in advance |
| Ranking skill | Per-event mean AUC 0.971, against 0.939 for ranking by elevation alone |
| Pooled gain over elevation | +0.038 (95% interval 0.019 to 0.061) over 50 events |
| Where it does not hold | Not shown under a 1 km spatial buffer or an out-of-time split. The model card says so. |

- **Model:** gradient boosting with monotonic constraints, chosen against logistic, XGBoost and a PyTorch physics-constrained neural network. The network violated the constraints, so I did not ship it.
- **Serving:** custom ONNX exporter (parity 3.3e-16), FastAPI service that verifies the model's SHA-256 before loading, rate limiting, security headers, hash-locked Docker image.
- **Engineering:** GitHub Actions gates for data, manifests and README claims, CodeQL, 96 test files, MLflow tracking on DagsHub, and a 58-row deviation register that tests enforce.
- **LLM layer:** an advisory service (Gemini, Groq fallback, deterministic template) behind an output guard, plus an MCP server and a LangGraph pipeline. One model passed my guard 6 of 6 times yet named the correct drivers 0 of 6, so driver text now comes only from the template.

Scores are rankings from a case-control sample. They are not flood probabilities, forecasts or official warnings.
---

## Other projects

| Project | What it is | Links |
|---|---|---|
| Loan Default Risk | Credit-default model on German Credit data (GradientBoosting). Cost-optimised threshold 0.22 from a 5:1 false-negative cost matrix. Test ROC-AUC 0.791, Gini 0.582, recall 0.833. I corrected my own overstated README metrics to these verified values. | [Code](https://github.com/jameskoero/loan-risk-assessment) / [App](https://jameskoero-loan-risk-assessment-h84.vercel.app/) |
| AfriSalaries | Salary-band classifier across 8 African markets (FastAPI, XGBoost, TF-IDF, SHAP). 1,526 real records, 59.5% band accuracy. Two regression designs rejected on validation grounds. | [Code](https://github.com/jameskoero/afrisalaries) / [App](https://afrisalaries.vercel.app) |
| SegmentIQ | K-Means customer segmentation, 5 segments, CSV batch upload (FastAPI, React). | [Code](https://github.com/jameskoero/kmeans-customer-segmentation) / [App](https://kmeans-customer-segmentation.vercel.app) |
| ChurchOS | Multi-tenant church management SaaS: JWT auth, 5-role access control, finance audit log, M-Pesa and Flutterwave integration. Phase 1 live. | [Code](https://github.com/jameskoero/ChurchOS) / [App](https://churchos-app.vercel.app) |
| Kenya at Gold | Open dataset and API on Kenya's 39 Olympic golds, with a four-dimension governance framework (FastAPI, SQLite). Code MIT, data CC-BY 4.0. | [Code](https://github.com/jameskoero/kenya-gold-ledger) / [Dashboard](https://kenya-gold-ledger.vercel.app) |
| Titanic Survival | Leak-free scikit-learn pipeline, hold-out ROC-AUC 0.8661 with bootstrap 95% intervals. | [Code](https://github.com/jameskoero/titanic-survival-prediction) / [DOI](https://doi.org/10.5281/zenodo.20387973) |

---

## Tech stack

- **ML:** Python, scikit-learn, XGBoost, PyTorch, ONNX Runtime, SHAP, pandas, NumPy
- **Validation:** leave-one-event-out and spatial cross-validation, leakage audits, bootstrap intervals
- **Geospatial:** Google Earth Engine, Sentinel-1 SAR, Copernicus GFM
- **MLOps:** GitHub Actions, MLflow, DagsHub, Docker, pytest, CodeQL, Dependabot
- **Backend and web:** FastAPI, Flask, React, PostgreSQL, SQLite, Render, Vercel
- **LLM and agents:** Gemini and Groq APIs, output guardrails, Model Context Protocol, LangGraph
- ---

## Currently

- Building Sokoni, a WhatsApp AI sales agent for Kenyan SMEs. The backend is scaffolded and the agent logic is not built yet.
- Learning retrieval-augmented generation and model fine-tuning. Nothing shipped yet.
- Open to remote Machine Learning Engineer, MLOps and Applied Scientist roles.

---

## Education and certifications

- B.Sc. Physics and Mathematics, Moi University, 2012
- Machine Learning using Python, Google Developers Launchpad (Certificate of Excellence), 2025
- Python Basics, Programiz, 2025

---

I came into ML from geophysics, where a wrong model can mean a wrong drilling decision. That is why every model I ship comes with what its number means, and what it does not.
