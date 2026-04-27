# purchasing-intention-of-online-shoppers
Problem Statement
Majestic is an e-commerce (marketplace) company that provides a wide range of products for customers. <br>
Over the past year, the company has achieved a conversion rate of only 15% from visitors to its website.<br>
During the pandemic period (2020–2021), according to data from the Digital Experience Benchmark Report, conversion rates across various e-commerce industries increased by an average of 28%, due to a significant shift in customer behavior toward online shopping. This presents a major opportunity for the company to increase its revenue.

Figure 1 – Average Conversion Rate for the E-commerce Industry

Objectives

To gain insights into customer behavior patterns while browsing the website.<br>
To predict whether visitors have a tendency to make a purchase or not.<br>
To provide appropriate business recommendations to increase customers’ likelihood of purchasing.

Goals

To build a machine learning model that can predict customers with the potential to generate revenue.
The model is expected to increase the Revenue Conversion Rate by 28%.

Business Metric

Revenue Conversion Rate

📂 Stage 1: Exploratory Data Analysis

Dataset
Table 1 – Dataset Summary

Descriptive Statistics

Figure 2 – Dataset Distribution
Figure 3 – Dataset Distribution with Boxplot

The results of descriptive statistical analysis for numerical features are as follows:

The overall data distribution tends to be positively skewed (Mean > Median). Features such as Administrative, Administrative_Duration, Informational, Informational_Duration, ProductRelated, ProductRelated_Duration, BounceRate, and PageValues have long distribution tails with values concentrated around 0. Based on these conditions and boxplot analysis, most features contain outliers.

Meanwhile, the descriptive statistical analysis for categorical features shows:

Some features have already been encoded, such as OperatingSystems, Browser, Region, and TrafficType. Therefore, additional data is required if interpretation is needed. Most visitors come from Region 2 and browse the website using Operating System type 2 with Browser type 1. Returning Visitors dominate the traffic. The "Other" value in the VisitorType feature needs to be handled. Two months (January and April) are missing in the Month feature. May has the highest number of visitors, followed by November.

Analysis

Figure 4 – Multivariate Analysis Heatmap

Correlation analysis results between features:

PageValues has a strong positive correlation with the target variable (Revenue). The higher the PageValues, the higher the likelihood of purchase. Meanwhile, BounceRates and ExitRates have a negative correlation with Revenue, meaning lower values increase revenue likelihood.

Some features exhibit multicollinearity, including:

ProductRelated with ProductRelated_Duration
Administrative with Administrative_Duration
Informational with Informational_Duration
BounceRates with ExitRates
Insight: Revenue Conversion Rate Based on Visitor Type

Figure 5 – Revenue Conversion Rate by Visitor Type

Around 80% of website visitors are Returning Visitors, indicating the company has successfully retained customers. However, the Revenue Conversion Rate is higher for New Visitors, with about 25% making purchases. In contrast, Returning Visitors have a lower conversion rate.

Further analysis would require additional data such as revenue or profit to determine which visitor type is more valuable. Based on these insights, business recommendations are needed to:

Increase conversion for Returning Visitors
Increase the number of New Visitors
Total Visitors per Month Based on Revenue

Figure 6 – Total Visitors per Month Based on Revenue

Traffic peaks in May, followed by November. However, despite high traffic, May has a low Revenue Conversion Rate of only 11%. In contrast, November has both high traffic and the highest conversion rate at 25%.

Stage 3: Data Pre-processing

Figure 7 – Data Pre-processing Workflow

Handling Missing and Duplicate Values
"Other" in VisitorType is replaced with the most frequent value: "Returning Visitor"
125 duplicate records were found and removed
Handling Outliers
Outliers account for 17.90% (Z-score analysis), which is significant
Outliers are retained, assuming they are not due to data errors
Feature Transformation
Log transformation is not used due to many zero values
PowerTransformer (Yeo-Johnson) is applied to normalize skewed data
Feature Encoding
VisitorType and Revenue are encoded using One Hot Encoding
Feature Extraction

New features created:

Duration per Administrative Page
Duration per Informational Page
Duration per ProductRelated Page
Feature Selection

Selected features based on relevance:

Duration per Page Administrative
Duration per Page Informational
ProductRelated
ExitRates
PageValues
SpecialDay
VisitorType_Returning_Visitor
Revenue_True
Train-Test Split
Data split: 70% training, 30% testing
Handling Class Imbalance
SMOTE applied to training data
Stage 4: Modeling and Evaluation

Random Forest with hyperparameter tuning is selected as the best model.

Evaluation

ROC-AUC is used to measure model performance (TPR vs FPR).

Table 2 – Random Forest Evaluation Results
Figure 8 – Confusion Matrix

The model achieves an ROC-AUC score of 0.90, indicating strong performance.

Feature Importance (SHAP Analysis)

Figure 9 – SHAP Feature Importance Bar Plot

Top 3 most influential features:

PageValues
ExitRates
ProductRelated

Figure 10 – SHAP Beeswarm Plot

Higher PageValues and ProductRelated → positive impact on purchase prediction
Higher ExitRates → negative impact
Stage 5: Business Insights & Recommendations
PageValues Insight

Figure 11 – PageValues Distribution
Table 3 – PageValues vs Conversion Rate

Visitors who purchase tend to visit pages with higher PageValues. Conversion can reach 56% when PageValues > 0, showing strong correlation.

ExitRates Insight

Figure 12 – ExitRates Distribution

Buyers tend to have lower ExitRates. The maximum observed value is 20%, which is acceptable compared to the industry average (<25%).

ProductRelated Insight

Figure 13 – ProductRelated Distribution

Average page views across industries: 5
ProductRelated page views exceed this average
Spending at least 50 seconds on a product page increases purchase probability
Machine Learning Prediction Workflow

Figure 14 – Early Purchase Prediction Workflow

This workflow predicts whether a visitor will purchase before the transaction occurs.

Business Recommendations
Based on Machine Learning
Provide product recommendations with higher PageValues
Improve page quality, content, and product ranking
Aim to increase Revenue Conversion Rate
Based on Insights
Run promotions and events during high-traffic/high-conversion months (May, March, November, December)
Increase New Visitor traffic (since their conversion is higher at 25%) by:
Offering special discounts for new users
Running advertisements to increase brand awareness
