# 🛒 Online Shoppers Purchasing Intention

---

## 📌 Stage 0: Problem Statement

Majestic is an e-commerce marketplace that provides a wide range of products for customers.  
Over the past year, the company has achieved a conversion rate of only **15%** from website visitors.

During the pandemic period (2020–2021), according to the *Digital Experience Benchmark Report*, e-commerce conversion rates increased by an average of **28%**, driven by a significant shift in customer behavior toward online shopping. This presents a major opportunity for the company to increase revenue.

---

## 🎯 Objectives
- Gain insights into customer browsing behavior on the website  
- Predict whether a visitor is likely to make a purchase  
- Provide business recommendations to improve conversion rates  

---

## 🚀 Goals
- Build a machine learning model to predict high-potential customers  
- Increase Revenue Conversion Rate by **28%**

---

## 📊 Business Metric
- **Revenue Conversion Rate**

---

## 📂 Stage 1: Exploratory Data Analysis (EDA)

### 📁 Dataset Overview
Table 1 – Dataset Summary  

---

### 📊 Descriptive Statistics

Figure 2 – Dataset Distribution  
Figure 3 – Dataset Distribution with Boxplot  

#### Key Findings (Numerical Features):
- Data distribution is **positively skewed (Mean > Median)**  
- Features such as Administrative, Informational, ProductRelated, and their durations have long-tailed distributions  
- Many features contain **outliers**, confirmed by boxplot analysis  

#### Key Findings (Categorical Features):
- Some variables are already encoded (OperatingSystems, Browser, Region, TrafficType)  
- Most visitors come from **Region 2**  
- Most users browse using **Operating System 2** and **Browser 1**  
- **Returning Visitors dominate traffic**  
- “Other” category in VisitorType requires handling  
- Missing months: **January and April**  
- Highest traffic months: **May**, followed by **November**

---

## 📈 Analysis

Figure 4 – Multivariate Correlation Heatmap  

### Key Insights:
- **PageValues** has a strong positive correlation with Revenue  
- **BounceRates** and **ExitRates** are negatively correlated with Revenue  
- Lower values of these features increase the likelihood of purchase  

### Multicollinearity detected in:
- ProductRelated ↔ ProductRelated_Duration  
- Administrative ↔ Administrative_Duration  
- Informational ↔ Informational_Duration  
- BounceRates ↔ ExitRates  

---

## 👥 Insight: Revenue Conversion Rate by Visitor Type

Figure 5 – Conversion Rate by Visitor Type  

- ~80% of visitors are **Returning Visitors**  
- However, **New Visitors have higher conversion rates (~25%)**  

### Insight:
- Returning Visitors dominate traffic but convert less  
- New Visitors convert better but are fewer in number  
- Additional revenue/profit data is needed for deeper analysis  

---

## 📅 Total Visitors per Month

Figure 6 – Monthly Visitor Distribution  

- Highest traffic: **May**, followed by **November**  
- May has low conversion rate (**11%**) despite high traffic  
- November shows the best performance with **25% conversion rate**

---

# 📂 Stage 3: Data Pre-processing

Figure 7 – Data Pre-processing Workflow  

## 🧹 1. Handling Missing & Duplicate Values
- “Other” in VisitorType → replaced with “Returning Visitor”  
- 125 duplicate records removed  

## 📉 2. Handling Outliers
- Outliers = **17.90% (Z-score analysis)**  
- Retained as they are assumed not to be data errors  

## 🔄 3. Feature Transformation
- Yeo-Johnson Power Transformation used  
- Handles skewed distributions and zero values effectively  

## 🏷️ 4. Feature Encoding
- One-Hot Encoding applied to:
  - VisitorType  
  - Revenue  

## 🔧 5. Feature Engineering
New features created:
- Duration per Administrative Page  
- Duration per Informational Page  
- Duration per Product Page  

## 🎯 6. Feature Selection
Final features used:
- Administrative Duration per Page  
- Informational Duration per Page  
- ProductRelated  
- ExitRates  
- PageValues  
- SpecialDay  
- VisitorType_Returning_Visitor  
- Revenue_True  

## ✂️ 7. Train-Test Split
- 70% training / 30% testing  

## ⚖️ 8. Class Imbalance Handling
- SMOTE applied to training data  

---

# 📂 Stage 4: Modeling & Evaluation

## 🤖 Model Used
- Random Forest (with Hyperparameter Tuning)

## 📊 Evaluation Metric
- ROC-AUC Score used for classification performance  

### Result:
- **ROC-AUC = 0.90** → Strong model performance  

Figure 8 – Confusion Matrix  

---

## 🌟 Feature Importance (SHAP Analysis)

Top 3 features:
1. PageValues  
2. ExitRates  
3. ProductRelated  

### Insights:
- Higher **PageValues** → higher purchase probability  
- Higher **ProductRelated** → positive impact  
- Higher **ExitRates** → negative impact  

---

# 📂 Stage 5: Business Insights & Recommendations

## 📌 PageValues Insight
Figure 11 – PageValues Distribution  

- Higher PageValues strongly correlate with purchases  
- Conversion rate reaches **56% when PageValues > 0**

---

## 📌 ExitRates Insight
Figure 12 – ExitRates Distribution  

- Buyers tend to have lower ExitRates  
- Maximum ExitRate (~20%) is within acceptable industry range (<25%)

---

## 📌 ProductRelated Insight
Figure 13 – ProductRelated Distribution  

- Average page views benchmark: **5**  
- Product pages exceed this benchmark  
- Users spending **≥50 seconds** on product pages have higher purchase probability  

---

## 🔮 Machine Learning Prediction Workflow

Figure 14 – Early Purchase Prediction Workflow  

A system designed to predict purchasing intent before the actual transaction occurs.

---

# 📢 Business Recommendations

## 🤖 Based on Machine Learning Model
- Recommend products with higher PageValues  
- Improve product page quality and ranking  
- Optimize content to increase engagement  

## 📊 Based on Business Insights
- Run campaigns during high-performing months:
  - May, March, November, December  
- Increase New Visitor acquisition:
  - Offer first-time user discounts  
  - Increase marketing and advertising efforts  
