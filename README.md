# Customer-Personality-Analysis
Marketing Campaign Response Prediction (2012–2014)
This project applies machine learning to evaluate past marketing campaign performance and predict which customers are most likely to respond to future campaigns. Using customer demographic, behavioral, and spending data (2012–2014), the analysis identifies high-performing customer segments and builds a predictive model to support more efficient targeting and improved conversion rates. 

Objectives
1. Evaluate historical campaign performance to understand what worked and identify responsive customer segments.
2. Build a predictive response model (Gradient Boosting) to identify potential responders for future campaigns. 

Dataset:
Source: UCI Machine Learning Repository (Marketing Campaign / Bank Marketing Campaign Data)
Size: 2,240 rows, 29 variables 
Target variable: Response (campaign acceptance) 
Feature categories include: demographics, household, spending behavior, purchasing activity, engagement history, and loyalty indicators. 

Tools & Libraries
- Python (Google Colab)
- pandas, numpy
- scikit-learn
- matplotlib & seaborn
- imbalanced-learn (SMOTE) 

Workflow
1) Data Preparation
   - Handled missing values (median for numeric, mode for categorical)
   - Removed unrealistic outlier income values (capped under 200,000)
   - Converted date fields and removed inactive/unreasonable records (e.g., age > 100) 
2) Feature Engineering
   Key engineered features include:
   - Total_Spending
   - Age, Age_Group
   - Total_Accepted_Campaigns
   - Is_Parent and total children in household
   - Customer_For (customer tenure)
   - Total_Purchases
   - Spending_Ratio (spend vs income) 
3) Exploratory Data Analysis (EDA)
- Identified strong imbalance in responders vs non-responders (~15% responders).
- Found key response patterns related to age, income, spending, recency, and tenure. 
4) Modeling & Evaluation
   Models compared:
   - Logistic Regression
   - Decision Tree
   - Random Forest
   - Gradient Boosting (with and without SMOTE)
     SMOTE was applied to improve detection of the minority responder class. 

Results (Model Selection)
Gradient Boosting + SMOTE was selected as the final model because it produced the best balance for predicting responders:
- Accuracy: 0.882
- Precision (Response=1): 0.62
- Recall (Response=1): 0.56
- F1-score (Response=1): 0.59 

Key Insights
1. High-income and high-spending customers are more likely to respond. 
2. Most responsive age segment: 30–59, with 40–49 as the highest engagement group. 
3. Customers with lower recency (more recent purchases) and longer tenure show higher response likelihood. 
4. Prior campaign acceptance (Total_Accepted_Campaigns) is a strong predictor of future response. 

Forecasting & Recommendations
1. Most customers have predicted response probability below 0.1, but 10–15% show probability > 0.4, forming a high-potential targeting segment.
2. Targeting the top 15% predicted responders may improve conversion rates by 8–10% while reducing ad spend by ~20%. 

Strategic Implications
- Retention Segment (High-Value Customers)
  Age 30–59, higher income, high spending, response probability > 0.4
  Recommended actions: premium loyalty offers, personalized email/campaigns within 30–45 days after purchase
- Growth Segment (Underperforming but Potential)
  Lower–mid income, shorter tenure, response probability 0.2–0.4
  Recommended actions: limited-time discounts, progressive targeting, cross-selling from strong categories
