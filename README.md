<div align="center">

<img src="assets/banner.svg" alt="James Koero, Machine Learning Engineer, Kisumu, Kenya. MLOps, geospatial and applied ML." width="100%">

<br>

<a href="https://nyando-flood-ai.vercel.app/"><img alt="Live dashboard" src="https://img.shields.io/badge/Live_dashboard-1ABC9C?style=for-the-badge&logo=vercel&logoColor=white"></a> <a href="https://github.com/jameskoero/nyando-flood-ai"><img alt="Source code" src="https://img.shields.io/badge/Source_code-181717?style=for-the-badge&logo=github&logoColor=white"></a> <a href="https://doi.org/10.5281/zenodo.23919053"><img alt="Zenodo DOI" src="https://img.shields.io/badge/Zenodo_DOI-1682D4?style=for-the-badge&logo=zenodo&logoColor=white"></a> <a href="https://www.linkedin.com/in/jameskoero"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"></a> <a href="https://orcid.org/0009-0001-8314-2682"><img alt="ORCID" src="https://img.shields.io/badge/ORCID-A6CE39?style=for-the-badge&logo=orcid&logoColor=white"></a>

</div>

<img src="assets/divider.svg" alt="" width="100%">

## 👋 Hello, I am James

**I build machine learning systems, then try to break them.** In 2026 I audited my own flood model, found that its headline metric was circular, retracted it, and rebuilt the whole system from real satellite data under strict leakage control. The rebuild is public, released as v2.0.0, and every number below can be re-derived from files in the repository.

I came to ML from physics and geophysics: B.Sc. Physics and Mathematics (Moi University), a geophysics attachment at KenGen Olkaria, then seven years in Kenyan insurance and investment distribution. Everything here was built on an Android phone with Termux and Google Colab, over mobile data.

**What I do**

- 🛰️ **Build end-to-end systems**, from raw satellite data to a live API and dashboard.
- 🧪 **Validate honestly:** event-based cross-validation, sealed test sets, and public retractions of my own results.
- 📦 **Ship reproducibly:** ONNX models verified by SHA-256, hash-locked Docker images, CI gates on data and claims.
- 🛡️ **Add LLMs safely:** output guards and deterministic fallbacks.
- 📐 **Use physics as a prior:** monotonic constraints and physical baselines.

<img src="assets/divider.svg" alt="" width="100%">

## 📊 Nyando Flood AI V2 at a glance

<div align="center">

<img alt="Per-event mean AUC: 0.971" src="https://img.shields.io/badge/Per--event_mean_AUC-0.971-1ABC9C?style=for-the-badge&labelColor=06172B"> <img alt="Gain over elevation: +0.038" src="https://img.shields.io/badge/Gain_over_elevation-%2B0.038-4DA3FF?style=for-the-badge&labelColor=06172B"> <img alt="Real samples: 4,420" src="https://img.shields.io/badge/Real_samples-4%2C420-8E7CFF?style=for-the-badge&labelColor=06172B"> <img alt="Sealed test events: 27" src="https://img.shields.io/badge/Sealed_test_events-27-C9A84C?style=for-the-badge&labelColor=06172B"> <img alt="Test files in CI: 96" src="https://img.shields.io/badge/Test_files_in_CI-96-F5A524?style=for-the-badge&labelColor=06172B"> <img alt="Deviation register: 58 rows" src="https://img.shields.io/badge/Deviation_register-58_rows-3DD68C?style=for-the-badge&labelColor=06172B">

Gain over elevation alone: 95% interval 0.019 to 0.061, pooled over 50 events. Sealed test: 27 held-out events, scored once. Data: 35 Sentinel-1 scene dates.

</div>

## 🌊 Flagship: Nyando Flood AI V2

An open-source system that ranks flood susceptibility across five wards of the Nyando basin in Kenya.

| What | Result |
|---|---|
| Data | Copernicus GFM labels and Google Earth Engine features. No synthetic data. |
| Sealed test | 27 held-out flood events, scored once under rules fixed in advance |
| Ranking skill | Per-event mean AUC 0.971, against 0.939 for ranking by elevation alone |
| Where it does not hold | Not shown under a 1 km spatial buffer or an out-of-time split. The model card says so. |

- **Model:** gradient boosting with monotonic constraints, chosen against logistic, XGBoost and a PyTorch physics-constrained neural network. The network violated the constraints, so I did not ship it.
- **Serving:** custom ONNX exporter (parity 3.3e-16), FastAPI service that verifies the model's SHA-256 before loading, rate limiting, security headers, hash-locked Docker image.
- **Engineering:** GitHub Actions gates for data, manifests and README claims, CodeQL, MLflow tracking on DagsHub, and a deviation register that tests enforce.
- **LLM layer:** an advisory service (Gemini, Groq fallback, deterministic template) behind an output guard, plus an MCP server and a LangGraph pipeline. One model passed my guard 6 of 6 times yet named the correct drivers 0 of 6, so driver text now comes only from the template.

> Scores are rankings from a case-control sample. They are not flood probabilities, forecasts or official warnings.

<img src="assets/divider.svg" alt="" width="100%">

## 🧰 Tech stack

**Machine learning**<br>
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikitlearn&logoColor=white) ![Gradient Boosting](https://img.shields.io/badge/Gradient_Boosting-0A1628?style=flat) ![XGBoost](https://img.shields.io/badge/XGBoost-FF6600?style=flat) ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white) ![SHAP](https://img.shields.io/badge/SHAP-C9A84C?style=flat) ![ONNX Runtime](https://img.shields.io/badge/ONNX_Runtime-005CED?style=flat&logo=onnx&logoColor=white) ![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)

**Validation and statistics**<br>
![Leave-one-event-out CV](https://img.shields.io/badge/Leave--one--event--out_CV-8E7CFF?style=flat) ![Spatial CV](https://img.shields.io/badge/Spatial_CV-8E7CFF?style=flat) ![Leakage audits](https://img.shields.io/badge/Leakage_audits-8E7CFF?style=flat) ![Bootstrap intervals](https://img.shields.io/badge/Bootstrap_intervals-8E7CFF?style=flat) ![Monotonic constraints](https://img.shields.io/badge/Monotonic_constraints-8E7CFF?style=flat) ![Model cards](https://img.shields.io/badge/Model_cards-8E7CFF?style=flat)

**Geospatial**<br>
![Google Earth Engine](https://img.shields.io/badge/Google_Earth_Engine-4285F4?style=flat&logo=google&logoColor=white) ![Sentinel-1 SAR](https://img.shields.io/badge/Sentinel--1_SAR-1F6FB2?style=flat) ![Copernicus GFM](https://img.shields.io/badge/Copernicus_GFM-0B4A52?style=flat) ![Remote sensing](https://img.shields.io/badge/Remote_sensing-4DA3FF?style=flat)

**MLOps and delivery**<br>
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=githubactions&logoColor=white) ![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat&logo=mlflow&logoColor=white) ![DagsHub](https://img.shields.io/badge/DagsHub-1F2937?style=flat) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white) ![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat&logo=pytest&logoColor=white) ![CodeQL](https://img.shields.io/badge/CodeQL-181717?style=flat&logo=github&logoColor=white) ![Dependabot](https://img.shields.io/badge/Dependabot-025E8C?style=flat&logo=dependabot&logoColor=white) ![Render](https://img.shields.io/badge/Render-46E3B7?style=flat&logo=render&logoColor=black) ![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white)

**Backend and web**<br>
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white) ![Flask](https://img.shields.io/badge/Flask-000000?style=flat&logo=flask&logoColor=white) ![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white) ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)

**LLM and agents**<br>
![Gemini API](https://img.shields.io/badge/Gemini_API-8E75B2?style=flat&logo=googlegemini&logoColor=white) ![Groq API](https://img.shields.io/badge/Groq_API-F55036?style=flat) ![Output guardrails](https://img.shields.io/badge/Output_guardrails-C0392B?style=flat) ![MCP](https://img.shields.io/badge/MCP-1C3C3C?style=flat) ![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat)

<img src="assets/divider.svg" alt="" width="100%">

## 🚀 More projects

<table>
<tr>
<td valign="top" width="50%">
<b>🏦 Loan Default Risk</b><br>
Credit-default model on German Credit data (GradientBoosting). Cost-optimised threshold 0.22 from a 5:1 false-negative cost matrix. Test ROC-AUC 0.791, Gini 0.582, recall 0.833. I corrected my own overstated README metrics to these verified values.<br>
<a href="https://github.com/jameskoero/loan-risk-assessment">Code</a> | <a href="https://jameskoero-loan-risk-assessment-h84.vercel.app/">App</a>
</td>
<td valign="top" width="50%">
<b>💰 AfriSalaries</b><br>
Salary-band classifier across 8 African markets (FastAPI, XGBoost, TF-IDF, SHAP). 1,526 real records, 59.5% band accuracy. Two regression designs rejected on validation grounds.<br>
<a href="https://github.com/jameskoero/afrisalaries">Code</a> | <a href="https://afrisalaries.vercel.app">App</a>
</td>
</tr>
<tr>
<td valign="top" width="50%">
<b>🥇 Kenya at Gold</b><br>
Open dataset and API on Kenya's 39 Olympic golds, with a four-dimension governance framework (FastAPI, SQLite). Code MIT, data CC-BY 4.0.<br>
<a href="https://github.com/jameskoero/kenya-gold-ledger">Code</a> | <a href="https://kenya-gold-ledger.vercel.app">Dashboard</a>
</td>
<td valign="top" width="50%">
<b>🏢 ChurchOS</b><br>
Multi-tenant church management SaaS: JWT auth, 5-role access control, finance audit log, M-Pesa and Flutterwave integration. Phase 1 live.<br>
<a href="https://github.com/jameskoero/ChurchOS">Code</a> | <a href="https://churchos-app.vercel.app">App</a>
</td>
</tr>
<tr>
<td valign="top" width="50%">
<b>🧩 SegmentIQ</b><br>
K-Means customer segmentation, 5 segments, CSV batch upload (FastAPI, React).<br>
<a href="https://github.com/jameskoero/kmeans-customer-segmentation">Code</a> | <a href="https://kmeans-customer-segmentation.vercel.app">App</a>
</td>
<td valign="top" width="50%">
<b>🚢 Titanic Survival</b><br>
Leak-free scikit-learn pipeline, hold-out ROC-AUC 0.8661 with bootstrap 95% intervals.<br>
<a href="https://github.com/jameskoero/titanic-survival-prediction">Code</a> | <a href="https://doi.org/10.5281/zenodo.20387973">DOI</a>
</td>
</tr>
</table>

<img src="assets/divider.svg" alt="" width="100%">

## 🎯 Currently

- Building Sokoni, a WhatsApp AI sales agent for Kenyan SMEs. The backend is scaffolded and the agent logic is not built yet.
- Learning retrieval-augmented generation and model fine-tuning. Nothing shipped yet.
- **Open to remote Machine Learning Engineer, MLOps and Applied Scientist roles.**

## 🎓 Education and certifications

- B.Sc. Physics and Mathematics, Moi University, 2012
- Machine Learning using Python, Google Developers Launchpad (Certificate of Excellence), 2025
- Python Basics, Programiz, 2025

> I came into ML from geophysics, where a wrong model can mean a wrong drilling decision. That is why every model I ship comes with what its number means, and what it does not.

<img src="assets/footer.svg" alt="Building from Kisumu, Kenya, one model at a time" width="100%">
