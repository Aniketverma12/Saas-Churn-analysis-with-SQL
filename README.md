# Saas-Churn-analysis-with-SQL
Saas Churn Analysis with SQL : Detect Customer Churn and Boost Retention 
📊 SaaS Churn Analysis with SQL
Detect Customer Churn and Boost Retention
🚀 Project Overview

Customer churn is one of the biggest challenges for SaaS businesses. This project analyzes subscription data using SQL to identify churn patterns, measure retention rates, and uncover actionable insights to reduce customer loss and increase long-term revenue.

The goal is to:

Detect churned customers

Calculate churn rate

Identify high-risk customer segments

Provide data-driven retention strategies

🎯 Objectives

Define and detect customer churn

Calculate Monthly Churn Rate

Analyze churn by:

Subscription plan

Customer tenure

Revenue segment

Identify trends leading to churn

Recommend strategies to improve retention

🗂️ Dataset Description

The dataset contains subscription-based SaaS customer information:

Column Name	Description
customer_id	Unique customer identifier
signup_date	Date when customer subscribed
subscription_plan	Plan type (Basic, Pro, Enterprise)
monthly_revenue	Monthly subscription amount
last_active_date	Last activity date
churn_date	Date customer cancelled (NULL if active)
country	Customer location
🧠 Key Business Definitions

Churned Customer:
A customer who cancelled their subscription within a given time period.

Churn Rate Formula:

𝐶
ℎ
𝑢
𝑟
𝑛
𝑅
𝑎
𝑡
𝑒
=
(
𝐶
𝑢
𝑠
𝑡
𝑜
𝑚
𝑒
𝑟
𝑠
𝐿
𝑜
𝑠
𝑡
𝐷
𝑢
𝑟
𝑖
𝑛
𝑔
𝑃
𝑒
𝑟
𝑖
𝑜
𝑑
/
𝐶
𝑢
𝑠
𝑡
𝑜
𝑚
𝑒
𝑟
𝑠
𝑎
𝑡
𝑆
𝑡
𝑎
𝑟
𝑡
𝑜
𝑓
𝑃
𝑒
𝑟
𝑖
𝑜
𝑑
)
∗
100
ChurnRate=(CustomersLostDuringPeriod/CustomersatStartofPeriod)∗100
🛠️ SQL Analysis Steps
1️⃣ Identify Churned Customers
SELECT customer_id, churn_date
FROM subscriptions
WHERE churn_date IS NOT NULL;
2️⃣ Calculate Overall Churn Rate
SELECT 
    COUNT(CASE WHEN churn_date IS NOT NULL THEN 1 END) * 100.0 
    / COUNT(*) AS churn_rate
FROM subscriptions;
3️⃣ Churn by Subscription Plan
SELECT 
    subscription_plan,
    COUNT(CASE WHEN churn_date IS NOT NULL THEN 1 END) AS churned_customers,
    COUNT(*) AS total_customers,
    COUNT(CASE WHEN churn_date IS NOT NULL THEN 1 END) * 100.0 
    / COUNT(*) AS churn_rate
FROM subscriptions
GROUP BY subscription_plan
ORDER BY churn_rate DESC;
4️⃣ Customer Tenure Analysis
SELECT 
    customer_id,
    DATEDIFF(churn_date, signup_date) AS tenure_days
FROM subscriptions
WHERE churn_date IS NOT NULL;
📈 Key Insights (Example)

Basic plan customers show higher churn compared to Enterprise.

Customers with tenure < 90 days are more likely to churn.

Low monthly revenue customers churn more frequently.

Certain regions show higher churn rates.

💡 Business Recommendations

Offer onboarding improvements for first 90 days.

Provide loyalty discounts for long-term customers.

Introduce personalized retention campaigns for high-risk segments.

Improve customer engagement tracking.

🧰 Tools Used

SQL (MySQL / PostgreSQL / SQL Server)

Excel / Power BI (Optional for visualization)

Database Management System

📊 Expected Outcomes

Clear churn percentage

Identification of high-risk customers

Plan-wise churn comparison

Data-backed retention strategy

📌 Future Improvements

Add predictive churn model using Python

Implement cohort analysis

Create automated churn dashboard

Integrate customer feedback analysis

👨‍💻 Author

Aniket Verma
Data Analysis Project – SaaS Churn Detection
