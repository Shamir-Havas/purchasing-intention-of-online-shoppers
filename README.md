# 🛒 Purchasing Intention of Online Shoppers

##  Problem Statement
Majestic is an e-commerce marketplace offering a wide range of products. Over the past year, the platform has achieved a conversion rate of only **15%** from website visitors.

During the pandemic (2020–2021), industry benchmarks reported an average **28% increase in conversion rates** due to a shift toward online shopping. This creates a strong opportunity to improve revenue performance.

---

##  Objectives
- Analyze customer behavior on the website  
- Predict whether a visitor will make a purchase  
- Provide business recommendations to improve conversion rates  

---

##  Goals
- Build a machine learning model to predict high-potential customers  
- Increase Revenue Conversion Rate by **28%**  

---

##  Business Metric
- **Revenue Conversion Rate**

---

## 📂 Project Workflow

###  Stage 1: Exploratory Data Analysis (EDA)

#### Key Findings:
- Data distribution is **positively skewed (Mean > Median)**  
- Most numerical features contain **outliers**  
- ~80% of visitors are **Returning Visitors**  
- Highest traffic occurs in **May and November**  

#### Insights:
- **PageValues** → Strong positive correlation with purchases  
- **ExitRates & BounceRates** → Negative correlation with purchases  
- **New Visitors convert more (25%)** than Returning Visitors  

---

### ⚙️ Stage 2: Data Pre-processing

#### Steps:
- Handle missing and duplicate values  
- Replace `"Other"` in VisitorType → `"Returning Visitor"`  
- Apply **Yeo-Johnson transformation** for skewed data  
- Perform **One-Hot Encoding**  
- Feature Engineering:
  - Duration per Administrative Page  
  - Duration per Informational Page  
  - Duration per Product Page  
- Handle class imbalance using **SMOTE**  
- Train-test split: **70:30**

---

### 🤖 Stage 3: Modeling & Evaluation

#### Model:
- **Random Forest (Hyperparameter Tuned)**  

#### Evaluation:
- **ROC-AUC Score: 0.90**

This indicates strong performance in distinguishing purchasing vs non-purchasing visitors.

---

### 📈 Feature Importance (SHAP)

Top features:
1. PageValues (positive impact)  
2. ExitRates (negative impact)  
3. ProductRelated (positive impact)  

---

## 💡 Business Insights

### 📌 PageValues
- Higher PageValues → Higher purchase probability  
- Conversion reaches **56% when PageValues > 0**

### 📌 ExitRates
- Lower ExitRates → Higher likelihood of purchase  

### 📌 Product Engagement
- Spending **≥ 50 seconds** on product pages increases conversion probability  

---

##  Machine Learning Use Case
Early prediction system to:
- Identify high-intent visitors  
- Enable real-time targeting and personalization  

---

## 📢 Business Recommendations

### 🔹 Based on Model
- Recommend high PageValue products/pages  
- Improve product page quality and ranking  

### 🔹 Based on Insights
- Run campaigns during:
  - May, March, November, December  
- Increase New Visitor acquisition:
  - First-time user discounts  
  - Marketing and advertising campaigns  

---

##  Conclusion
This project demonstrates how machine learning can:
- Predict purchasing intent  
- Improve customer targeting  
- Increase Revenue Conversion Rate  

With a strong model performance (**ROC-AUC: 0.90**), this solution has high potential to drive business growth.
