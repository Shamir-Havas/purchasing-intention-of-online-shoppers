# 🛒 ONLINE SHOPPERS PURCHASING INTENTION

### **Predicting whether an online visitor is likely to make a purchase**

> An end-to-end **EDA → Preprocessing → Feature Engineering → Machine Learning → Model Interpretation → Business Recommendations** project.

---

## 📌 PROJECT OVERVIEW

Majestic is an e-commerce marketplace with a **15% website conversion rate**. This project analyzes online visitor behavior and develops a machine learning approach to identify sessions with higher purchase potential.

### 🎯 OBJECTIVES

- **UNDERSTAND** customer browsing behavior
- **IDENTIFY** factors associated with purchasing
- **PREDICT** purchase intention
- **TRANSLATE** model findings into business recommendations

### 📊 BUSINESS METRIC

**Revenue Conversion Rate**

---

## 📂 DATASET

- **12,330** online shopping sessions
- **18** features
- Target: **Revenue**
- **125 duplicate records** identified and removed
- Class imbalance addressed during preprocessing

---

## 🔍 EXPLORATORY DATA ANALYSIS

### KEY FINDINGS

- Numerical variables are generally **positively skewed** with long-tailed distributions.
- Many numerical features contain **outliers**.
- **Returning Visitors** dominate traffic.
- **New Visitors** show a higher conversion rate of approximately **25%**.
- **May** has the highest traffic, while **November** shows the strongest conversion performance at approximately **25%**.
- **PageValues** has a strong positive relationship with Revenue.
- **BounceRates** and **ExitRates** show negative relationships with Revenue.

### ⚠️ MULTICOLLINEARITY

- `ProductRelated` ↔ `ProductRelated_Duration`
- `Administrative` ↔ `Administrative_Duration`
- `Informational` ↔ `Informational_Duration`
- `BounceRates` ↔ `ExitRates`

---

## ⚙️ DATA PREPROCESSING

### 🧹 DATA CLEANING

- Replaced **"Other" VisitorType** with **"Returning Visitor"**
- Removed **125 duplicate records**
- Investigated outliers using **Z-score analysis**
- Retained identified outliers where they were considered valid observations

### 🔄 TRANSFORMATION & FEATURE ENGINEERING

- Applied **Yeo-Johnson Power Transformation** to address skewness
- Applied **One-Hot Encoding** to categorical variables
- Created duration-per-page features for:
  - **Administrative pages**
  - **Informational pages**
  - **Product pages**
- Reduced redundancy caused by highly correlated variables

### ⚖️ TRAINING SETUP

- **70% Training / 30% Testing**
- **SMOTE** applied to the training data

---

## 🤖 MACHINE LEARNING MODEL

Multiple classification approaches were evaluated, with **Random Forest** selected as the final model after hyperparameter tuning.

### 🏆 MODEL PERFORMANCE

| METRIC | RESULT |
|---|---:|
| **ROC-AUC** | **0.90** |

**ROC-AUC = 0.90** indicates strong ability to distinguish between purchasing and non-purchasing sessions.

---

## 🌟 MODEL INTERPRETATION — SHAP

SHAP analysis was used to understand **which features most influenced model predictions**.

### 🔝 TOP 3 FEATURES

1. **PageValues**
2. **ExitRates**
3. **ProductRelated**

### 💡 MODEL INSIGHTS

- **Higher PageValues** → stronger purchase signal
- **Higher ProductRelated activity** → positive contribution toward purchase prediction
- **Higher ExitRates** → negative contribution toward purchase prediction

---

## 💼 BUSINESS INSIGHTS

### 💰 PAGEVALUES

- Higher **PageValues** are strongly associated with purchases.
- Conversion reaches approximately **56% when PageValues > 0**.

### 🚪 EXIT RATES

- Buyers tend to have **lower ExitRates**.

### 🛍️ PRODUCT ENGAGEMENT

- Product pages receive substantial visitor activity.
- Sessions with **≥50 seconds** spent on product pages show higher purchase probability in the analysis.

### 👥 VISITOR TYPE

- Returning Visitors dominate traffic.
- New Visitors convert at a higher rate but represent a smaller share of traffic.

---

## 📢 BUSINESS RECOMMENDATIONS

### 🤖 MODEL-DRIVEN

- Prioritize products and sessions associated with **higher PageValues**.
- Improve **product-page quality and ranking**.
- Optimize content to increase **visitor engagement**.

### 📊 DATA-DRIVEN

- Focus campaigns around **high-performing months**, including May, March, November, and December.
- Increase **New Visitor acquisition** through targeted marketing.
- Consider **first-time visitor offers or discounts** to encourage conversion.

---

## 🔄 PROJECT WORKFLOW

```text
RAW DATA
   ↓
EXPLORATORY DATA ANALYSIS
   ↓
DATA CLEANING
   ↓
FEATURE ENGINEERING
   ↓
TRANSFORMATION & ENCODING
   ↓
SMOTE / TRAIN-TEST SPLIT
   ↓
RANDOM FOREST + HYPERPARAMETER TUNING
   ↓
MODEL EVALUATION
   ↓
SHAP INTERPRETATION
   ↓
BUSINESS INSIGHTS & RECOMMENDATIONS
```

---

## 🛠️ TECHNOLOGIES

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **XGBoost**
- **SHAP**
- **Jupyter Notebook**

---

## 📁 PROJECT STRUCTURE

```text
online-shoppers-purchasing-intention/
│
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_preprocessing.ipynb
│   └── 03_modeling.ipynb
│
└── README.md
```

---

## 🎯 KEY TAKEAWAY

This project demonstrates an **end-to-end machine learning workflow** for an e-commerce purchase-intention problem — from understanding visitor behavior and preparing the data to building a predictive model, interpreting its decisions, and converting the findings into actionable business recommendations.

---

## 👤 AUTHOR

### **SHAMIR HAVAS**

**Aspiring Data Scientist | Machine Learning | Data Analytics**
