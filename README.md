# 🎓 Extended Student Performance Factors Analysis

## 📌 Project Overview

**Extended Student Performance Factors Analysis** is a data analysis project that looks at which student factors are most strongly associated with **exam scores**. It builds on Part 1 with a regression model and statistical tests to check whether the patterns we saw hold up.

The project combines **Lasso Regression**, **5-fold Cross-Validation**, **Spearman Correlation**, **ANOVA**, and **Chi-Square Tests**.

This is a course project (CSMODEL). It reports **associations** in one dataset. It does not show that any factor *causes* higher or lower scores.

**Part 1 of Student Performance Factors Analysis:** [LINK](https://github.com/markcelemen/csmodel-mco1)

**Presentation slides:** [View Project Slides on Canva](https://www.canva.com/design/DAG5hqcDa10/F9KLvrYEC_WnpkwNo5IcDw/view?utm)

---

## 💡 Key Skills Developed

* **Data Cleaning & Preprocessing**
* **Exploratory Data Analysis (EDA)**
* **Statistical Inference** (Spearman correlation, ANOVA, Chi-Square, Shapiro-Wilk normality checks)
* **Regression Modeling** (Lasso Regression + Cross-Validation)
* **Data Visualization** (Matplotlib, Seaborn)
* **Python Data Science Stack** (NumPy, Pandas, SciPy, Scikit-Learn)
* **Interpretation of Statistical Outputs**

---

## 📊 Dataset Details

**Source:** Kaggle — *Student Performance Factors Dataset*  
**Dataset link:** [https://www.kaggle.com/datasets/lainguyn123/student-performance-factors](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors)

* **Rows:** 6,607 (6,464 after cleaning)
* **Columns:** 20 (19 predictors + `Exam_Score`)
* Variables include study hours, attendance, parental involvement, teacher quality, resource access, previous scores, and more.
* We did not verify how the original data was collected.

---

## 🎯 Problem Statement

Student outcomes are shaped by many things at once. This project asks:

* Which student behaviors are most strongly associated with exam scores?
* Is access to educational resources associated with exam scores?
* Do study hours, attendance, and teacher quality relate to exam scores?
* How well can a regression model predict exam scores from these factors?

---

## 🏫 Possible Use Cases

These are intended applications. We did not test any of them.

* **Educational Institutions:** Spot patterns that could inform student support programs.
* **Teachers & Mentors:** Understand which behaviors tend to go with higher scores.
* **Researchers:** Starting point for further, more controlled studies.

---

## 🛠️ Approach

1. **Data Cleaning**
   * Dropped 143 rows missing `Teacher_Quality` or `Distance_from_Home` (6,607 → 6,464).
   * Filled missing `Parental_Education_Level` with `"None"`. This assumes a blank means no formal education, which we did not verify.
   * Checked categorical columns for inconsistent labels (none found).
   * Capped one exam score of 101 to 100.
2. **Regression Modeling**
   * Lasso Regression, 70/30 train/test split, alpha chosen by 5-fold cross-validation.
3. **Statistical Inference**
   * Shapiro-Wilk on 500-row samples to check normality. Exam scores were not normal, so we used **Spearman** correlation instead of Pearson.
   * ANOVA and Chi-Square tests for group comparisons.
4. **Interpretation**
   * Compared regression coefficients against the significance tests and noted where they disagreed.

---

## 🔍 Analysis Steps

### **1. Lasso Regression Modeling**

* Selected alpha: 0.0028 (via 5-fold CV)
* Test RMSE: **2.03** points (0–100 scale), test R²: **0.72** (train R²: 0.72)
* Largest coefficients: Attendance (2.30), Hours Studied (1.78)
* Only 6 of 24 encoded features were shrunk to near zero. The other 18 kept non-zero coefficients.
* Caveat: categorical features were target-encoded and numeric ones were standardized, so coefficients are not directly comparable across the two groups. When we re-fit with every feature standardized and ordinal categories coded in order, Attendance (2.29) and Hours Studied (1.76) were still the top two.

### **2. Statistical Inference**

#### ✓ **Spearman Correlation with Exam Score**

* Hours Studied: ρ = **0.483**, p < 0.001
* Attendance: ρ = **0.673**, p < 0.001
* Teacher Quality (coded Low=0, Medium=1, High=2): ρ = **0.081**, p = 6.6e−11. This is a weak positive association.

#### ✓ **ANOVA**

* Exam score by Access to Resources: F = 94.12, p = 5.1e−41. Mean scores were 66.2 (Low), 67.1 (Medium), 68.1 (High), about a 1.9-point gap between Low and High.
* Exam score by Study Hour group: F = 216.21, p = 1.57e−289

#### ✓ **Chi-Square Test**

* Study Hours × Access to Resources: p = 0.577. We found no association between how long students studied and their resource access. Some hour groups are very small (the 41+ group has 2 students).

---

## 🏆 Results & Deliverables

### **Key Findings**

* **Attendance** has the strongest association with exam scores (Spearman 0.67), and the largest Lasso coefficient.
* **Hours studied** is also clearly associated with exam scores (Spearman 0.48). Scores differ significantly across study-hour groups.
* **Resource access** is associated with a small but statistically significant difference in scores (about 1.9 points, Low vs. High).
* **Teacher quality**, as measured in this dataset, shows only a weak association with scores.
* **Study hours and resource access** showed no detectable association in this data.

These are correlations. They do not show that studying more, attending more, or having more resources *causes* higher scores. We did not measure motivation against study hours, so we make no claim about it.

### **Project Deliverables**

* ✔ Cleaned dataset
* ✔ Lasso regression model with cross-validation, plus actual-vs-predicted and residual plots
* ✔ Statistical tests (Spearman, ANOVA, Chi-Square) with written interpretations
* ✔ Insights and conclusions section in the notebook

---

## ⚠️ Known Issues

* **Teacher quality (notebook cells on "Teacher Quality vs Exam Score").** The notebook's correlation output for this test is `nan`, and its written text reports r = −0.055 and a "paradox" with the Lasso result. That value only reproduces if Low/Medium/High are coded alphabetically (High=0, Low=1, Medium=2). With the correct order, the correlation is +0.081, which agrees with the Lasso direction. This README uses the corrected value. The notebook has not been fixed yet.
* **Some saved notebook outputs differ from the written text** (for example, resource ANOVA F = 98.00 and hour-group F = 220.22 in saved output, versus 94.12 and 216.21 in the text). Re-running on the cleaned data gives the values in this README.
* **Lasso interpretation.** The notebook text says only two predictors were significant. Lasso kept 18 of 24 features with non-zero coefficients. Attendance and Hours Studied are the two largest, not the only ones.
* We have not answered whether there is a point where more study hours stop helping.

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
category_encoders
```

---

## ▶️ Usage

### **Open the Notebook in Google Colab**

* Upload the repo
* Open: `CSMODEL_MCO2.ipynb`
* Run all cells (the Google Drive mount cell can be skipped if the CSV is uploaded directly)

### **To run locally via Jupyter**

```bash
jupyter notebook
```

---

## 🔮 Future Enhancements

* Fix the teacher quality encoding in the notebook and re-run that section
* Standardize all features before comparing Lasso coefficients
* Test additional models (Random Forest, Gradient Boosting, Ridge, ElasticNet)
* Include `Previous_Scores` and `Tutoring_Sessions` in the discussion. Both rank high once features are on the same scale.
* Check the effect of study hours across groups to see whether gains level off
* Interactive dashboards (Plotly, Streamlit)

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
