# 🎓 EdTech Learning Analytics: Predicting Student Dropout & Academic Success

**Author:** Hansi Weerakoon  
**Role:** Data Science Undergraduate, SLIIT  
**Domain:** EdTech / Learning Analytics / Predictive Modeling  

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Manipulation-orange)](https://pandas.pydata.org/)
[![SciPy](https://img.shields.io/badge/SciPy-Statistical%20Testing-green)](https://scipy.org/)
[![PowerBI](https://img.shields.io/badge/PowerBI-Dashboarding-yellow?logo=powerbi)](https://powerbi.microsoft.com/)

---

## 🌟 Project Overview

In the higher education sector, student retention is a critical challenge. When students drop out, institutions lose tuition revenue, and students lose time and potential. This project builds an **end-to-end predictive analytics pipeline** designed for an **EdTech / Student Success** context. 

By combining rigorous statistical hypothesis testing with machine learning, this project identifies early warning signals of student attrition. The goal is to transition university advising from a *reactive* model to a *proactive* one, allowing academic advisors to intervene before a student reaches the point of no return.

---

## 📊 The Dataset

- **Source:** Predict Students' Dropout and Academic Success dataset, originally published in the MDPI Data Journal and hosted on the UCI Machine Learning Repository.(https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success) 
- **Records:** 4,424 student profiles
- **Features:** 36 demographic, socioeconomic, and academic enrollment attributes
- **Target Variable:** `Graduate` (50%) | `Dropout` (32%) | `Enrolled` (18%)
- **Context:** Data originates from Portuguese higher education institutions, featuring diverse courses from Health Sciences to STEM and Humanities.

---

## 🔬 The Data Science Pipeline

Unlike standard projects that jump straight into modeling, this pipeline prioritizes **data integrity, domain context, and statistical validation**.

### Phase 1: Semantic Data Audit & Decoding
Raw datasets often lack context. I mapped all 36 heavily label-encoded variables back to human-readable categories using the official UCI/MDPI data dictionary. High-cardinality features (like 44 distinct parent education codes) were logically binned into actionable buckets (e.g., `Basic/Secondary`, `Higher Education`) to prevent model overfitting and improve interpretability.

### Phase 2: Domain-Driven Feature Engineering
Created behavioral and socioeconomic flags that capture the *reality* of the student experience:
- `Financial_Risk_Flag`: Binary indicator for students who are debtors OR have unpaid tuition.
- `First_Generation_Student`: Flags students whose parents only have Basic/Secondary education.
- `Evaluation_Load_Ratio`: Calculated as `Evaluations / Enrolled Courses`. A ratio > 1.0 indicates a student is taking more exams than they are currently enrolled in (a strong proxy for retaking failed modules).
- `Pass_Rate_1st_Sem` & `Pass_Rate_2nd_Sem`: Academic momentum indicators.

### Phase 3: Statistical Hypothesis Testing
Before training any models, I conducted **10 independent hypothesis tests** (Chi-Square & Independent T-Tests) to mathematically prove which features actually impact student success (α = 0.05). *All 10 hypotheses were rejected, confirming high feature significance.*

### Phase 4: Predictive Modeling Strategy
- **Models:** Random Forest & XGBoost (Tree-based models chosen for handling non-linear interactions and providing feature importance).
- **Primary Metric:** **Recall for the Dropout class**. In EdTech, a *False Negative* (failing to flag an at-risk student) is much more damaging than a *False Positive* (checking in on a student who is actually fine).
- **Imbalance Handling:** Addressed via `class_weight='balanced'` to preserve raw data integrity without synthetic oversampling.

### Phase 5: Business Intelligence Dashboard
Translating model outputs into an interactive **Power BI Dashboard** for University Deans and Advisors, featuring cohort monitoring, demographic breakdowns, and feature-impact visualizations.

---

## 💡 Key Statistical Findings

> *These insights were validated through rigorous Chi-Square and T-Testing (p < 0.05).*

- 💰 **Financial Vulnerability is the #1 Predictor:** Students flagged with `Financial_Risk_Flag = 1` are **4x more likely** to dropout compared to fully supported peers (Chi-square p < 0.001).
- 📉 **The STEM Crisis:** STEM programs have a mere **13% graduation rate**, while Health Sciences boast a **63.6% graduation rate** (p < 0.001). This signals a critical need for curriculum review or enhanced tutoring in STEM faculties.
- 📚 **The Engagement Paradox:** Counter-intuitively, graduates enroll in *more* courses on average (**6.67**) than dropouts (**5.82**). This proves that a higher course load is a proxy for student engagement and momentum, not "academic overload".
- 🔄 **Academic Momentum & Retakes:** Dropouts have a significantly higher `Evaluation_Load_Ratio` (1.27 vs 1.21). This indicates they are taking more assessments per course, likely due to the burden of retaking failed modules from previous semesters.
- 🎓 **The First-Generation Gap:** Students flagged as `First_Generation_Student` show a statistically significant higher dropout rate, highlighting the need for targeted mentorship programs.

---

## 🛠 Tech Stack

| Layer | Tools & Libraries |
|-------|-------------------|
| **Data Processing** | Python, Pandas, NumPy |
| **Statistical Analysis** | SciPy (`chi2_contingency`, `ttest_ind`), Statsmodels |
| **Machine Learning** | scikit-learn (`RandomForestClassifier`, `StandardScaler`, `classification_report`) |
| **Visualization** | Matplotlib, Seaborn |
| **Business Intelligence** | Power BI Desktop, DAX |
| **Environment** | Jupyter Notebook, Google Colab |
| **Version Control** | Git, GitHub |

---

## 📁 Repository Structure

```text
📦 Student_Dropout_Prediction
├── 📄 README.md                  # Project documentation (You are here!)
├── 📂 data/
│   ├── 📄 Raw_Dataset.csv        # Original UCI/Kaggle dataset
│   └── 📄 Cleaned_Dataset.csv    # Post-preprocessing & feature engineering
├── 📂 notebooks/
│   ├── 📓 01_EDA_and_Data_Audit.ipynb                       # Exploratory Data Analysis
│   ├── 📓 02_Preprocessing_and_Feature_Engineering.ipynb    # Data Cleaning & Binning
│   ├── 📓 03_Hypothesis_Testing.ipynb                       # Statistical Validation (10 Tests)
│   └── 📓 04_Model_Training_and_Evaluation.ipynb            # ML Models (Coming Soon)
├── 📂 dashboard/
│   └── 📊 Student_Success_Dashboard.pbix                    # Power BI File
└── 📄 requirements.txt           # Python dependencies
```
---

📬 Connect with Me
If you're interested in EdTech, Learning Analytics, or Data Science, let's connect!
- 🔗 LinkedIn: linkedin.com/in/hansi-weerakoon
- 🔗 GitHub: github.com/hansi-weerakoon
- 📧 Email: hnweerakoon@gmail.com
  
© 2026 Hansi Weerakoon. Built for academic and portfolio purposes.
