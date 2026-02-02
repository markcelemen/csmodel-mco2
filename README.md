# 🎓 Extended Student Performance Factors Analysis

## 📌 Project Overview

**Extended Student Performance Factors Analysis** is a comprehensive analytics project designed to uncover the key factors influencing **student academic performance**. Using **data modeling**, **statistical inference**, and **exploratory data analysis**, the project extends beyond surface-level insights by identifying statistically significant relationships between behavioral, socioeconomic, and academic variables.

The project combines **Lasso Regression**, **Cross-Validation**, **ANOVA**, **Chi-Square Tests**, and **Correlation Analysis** to validate findings and guide evidence-based educational strategies. 

**Part 1 of Student Performance Factors Analysis:** [LINK](https://github.com/markcelemen/csmodel-mco1)

**Presentation slides:** [View Project Slides on Canva](https://www.canva.com/design/DAG5hqcDa10/F9KLvrYEC_WnpkwNo5IcDw/view?utm)

---

## 💡 Key Skills Developed

* **Data Cleaning & Preprocessing**
* **Exploratory Data Analysis (EDA)**
* **Statistical Inference (t-tests, ANOVA, Chi-Square)**
* **Regression Modeling** (Lasso Regression + Cross-Validation)
* **Data Visualization** (Matplotlib, Seaborn)
* **Python Data Science Stack** (NumPy, Pandas, SciPy, Scikit-Learn)
* **Interpretation of Statistical Outputs**

---

## 📊 Dataset Details

**Source:** Kaggle — *Student Performance Factors Dataset*  
**Dataset link:** [https://www.kaggle.com/datasets/lainguyn123/student-performance-factors](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors)

* **Rows:** 6,607
* **Columns:** 29
* Variables include study hours, attendance, parental background, teacher quality, resource access, exam scores, and more.

---

## 🎯 Problem Statement

Educational challenges are often complex and influenced by behavioral, socioeconomic, and environmental factors. This project aims to identify:

* Which student behaviors significantly affect exam performance
* Whether socioeconomic access impacts academic outcomes
* Whether study habits, attendance, and teacher quality statistically predict exam scores
* How to build a predictive framework for understanding performance patterns

---

## 🏫 Use Cases

* **Educational Institutions:** Identify performance gaps and design targeted student support programs. 🏫
* **Teachers & Mentors:** Personalize teaching approaches based on behavioral and socioeconomic trends. 👩‍🏫
* **Policy Makers:** Develop policies to support low-income students and bridge access inequalities. 📚
* **Researchers:** Explore data-driven methods to predict and enhance academic outcomes. 🔬

---

## 🛠️ Approach

1. **Data Cleaning & Feature Preparation**
2. **Exploratory Data Analysis** (distribution, correlations, trends)
3. **Regression Modeling**

   * Lasso Regression
   * 5-Fold Cross-Validation (hyperparameter tuning for α)
4. **Statistical Inference**

   * Correlation tests
   * ANOVA
   * Chi-Square Tests
   * Hypothesis Testing
5. **Interpretation & Cross-Validation of Findings**

   * Compare regression coefficients vs. significance tests
   * Identify discrepancies and confounding variables

---

## 🔍 Analysis Steps

### **1. Exploratory Data Analysis (EDA)**

* Distribution of exam scores
* Study habits, attendance patterns, and behavior trends
* Heatmaps & pairplots for variable relationships

### **2. Lasso Regression Modeling**

* Identified most influential predictors
* Tuned hyperparameters using **5-fold cross-validation**
* Evaluated RMSE & residual patterns

### **3. Statistical Inference**

Validated regression findings through rigorous hypothesis tests:

#### ✓ **Correlation Tests**

* Hours Studied ↗ Exam Score (r = **0.483**, p ≪ 0.05)
* Attendance ↗ Exam Score (r = **0.673**, p ≪ 0.05)

#### ✓ **ANOVA**

* Access to Educational Resources impacts exam performance

  * *F = 94.12, p = 5.109e−41*
* Study Hour Bins significantly affect exam scores

  * *F = 216.21, p = 1.57e−289*

#### ✓ **Chi-Square Test**

* Study Hours × Access to Resources → **no significant relationship**

  * *p = 0.577*
    → Resources don’t dictate how long students study.

#### ✓ **Teacher Quality Paradox**

* Weak negative correlation (r = −0.055, p ≪ 0.05)
* Contradicts Lasso’s positive coefficient → potential confounders

---

## 🏆 Results & Deliverables

### **Key Findings**

* **Attendance** is the strongest positive predictor of exam performance.
* **Study time** significantly increases exam scores, even across grouped intervals.
* **Resource access** positively affects academic achievement.
* **Teacher quality**, as measured in this dataset, shows minimal predictive power.
* **Study hours** are *independent* of access to resources — motivation-driven behavior.

### **Project Deliverables**

* ✔ Clean, processed dataset
* ✔ Complete EDA analysis
* ✔ Lasso regression model + cross-validation
* ✔ Statistical inference suite (ANOVA, Chi-Square, correlations, hypothesis tests)
* ✔ Visualizations for all test results
* ✔ Final insights & interpretation report

---

## 💻 Installation

### **1. Clone the Repository**

```bash
git clone https://github.com/markcelemen/csmodel-mco2.git
cd csmodel-mco2
```

### **2. Install Dependencies**

```bash
pip install -r requirements.txt
```

Or manually:

```
pandas
numpy
matplotlib
seaborn
scikit-learn
scipy
```

---

## ▶️ Usage

### **Open the Notebook in Google Colab**

* Upload the repo
* Open: `CSMODEL_MCO2.ipynb`
* Run all cells

### **To run locally via Jupyter**

```bash
jupyter notebook
```

---

## 🔮 Future Enhancements

* Machine Learning models (Random Forest, XGBoost, Gradient Boosting)
* Predictive modeling for student risk scoring
* Interactive dashboards (Plotly, Power BI, Streamlit)
* Feature engineering (interaction terms, socioeconomic clusters)
* Multi-model comparison (Ridge, ElasticNet, Linear Regression)

---

## 🤝 How to Contribute

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Open a pull request

---

## 👥 Team

* Mark Celemen
* Rei Encallado
* Andrei Gildore
* Hannah Lee
* Khyle Villorente
