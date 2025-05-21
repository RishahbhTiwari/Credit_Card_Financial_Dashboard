💳 Credit Card Financial Dashboard (Power BI + SQL + DAX)-

📌 Project Objective:
To develop a real-time, interactive Credit Card Financial Dashboard that delivers weekly insights into key performance metrics like revenue, transactions, customer trends, and card usage. This solution enables stakeholders to monitor performance, track growth, and make data-driven decisions.
----------------------------------------------------------------------------------------------------------------------------------

🧰 Tools & Technologies Used:
Tool/Tech	                        Purpose
Power BI	                        Interactive dashboards and data modeling
PostgreSQL	                      Real-time backend database
SQL	                              Data extraction and transformation
DAX (Data Analysis Expressions)	  Business logic, KPIs, and custom metrics
Excel	                            Initial data staging and structure
----------------------------------------------------------------------------------------------------------------------------------

🗂️ Project Components:
Data Sources: Customer info, transaction history, card type, location
SQL Integration: Data imported into PostgreSQL using CSVs and queried in Power BI
Data Modeling: Relationships created across fact and dimension tables
Calculated Columns/Measures: Using DAX for revenue, customer segments, trends
Weekly Insights: Week-over-week performance tracking
Dashboards: Built with slicers, charts, KPIs for executive-level summaries
----------------------------------------------------------------------------------------------------------------------------------

🔢 DAX Measures & Custom Logic:
-- Categorize age groups
AgeGroup = SWITCH(
    TRUE(),
    'cust_detail'[customer_age] < 30, "20-30",
    'cust_detail'[customer_age] >= 30 && 'cust_detail'[customer_age] < 40, "30-40",
    'cust_detail'[customer_age] >= 40 && 'cust_detail'[customer_age] < 50, "40-50",
    'cust_detail'[customer_age] >= 50 && 'cust_detail'[customer_age] < 60, "50-60",
    'cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)

-- Categorize income groups
IncomeGroup = SWITCH(
    TRUE(),
    'cust_detail'[income] < 35000, "Low",
    'cust_detail'[income] >= 35000 && 'cust_detail'[income] <70000, "Medium",
    'cust_detail'[income] >= 70000, "High",
    "unknown"
)

-- Revenue metrics
Revenue = 'cc_detail'[annual_fees] + 'cc_detail'[total_trans_amt] + 'cc_detail'[interest_earned]

Current_week_Revenue = CALCULATE(
    SUM('cc_detail'[Revenue]),
    FILTER(ALL('cc_detail'), 'cc_detail'[week_num2] = MAX('cc_detail'[week_num2]))
)

Previous_week_Revenue = CALCULATE(
    SUM('cc_detail'[Revenue]),
    FILTER(ALL('cc_detail'), 'cc_detail'[week_num2] = MAX('cc_detail'[week_num2]) - 1)
)
----------------------------------------------------------------------------------------------------------------------------------

📊 Key Insights from Dashboard (Week 53):
📈 Week-over-Week Change:
    Revenue increased by 28.8%
    Transaction Volume and Count increased significantly
    Customer Count also saw a positive jump
📅 Year-to-Date Overview:
    💰 Total Revenue: $57M
    💳 Total Transaction Amount: $46M
    💼 Total Interest Earned: $8M
👨‍💼 Revenue by Gender:
    Male: $31M
    Female: $26M
🏦 Card Type Usage:
    Blue & Silver cards account for 93% of all transactions
🌍 Top States by Revenue:
    Texas, New York, and California contribute to 68% of total revenue
📈 Activation Rate: 57.5%
⚠️ Delinquency Rate: 6.06%
----------------------------------------------------------------------------------------------------------------------------------

🖥️ Dashboard Features:
    ✅ Weekly revenue tracking with dynamic filters
    🧠 Customer segmentation by age, gender, income, marital status
    🌐 Geographic heatmaps and bar charts by city/state
    🏷️ Card-type usage trends with slicers
    ⏳ Time-based performance metrics (YTD, WoW, etc.)
----------------------------------------------------------------------------------------------------------------------------------

🔌 Real-Time Integration via PostgreSQL:
    Structured multiple CSVs into relational tables
    Wrote SQL queries to extract transactional and demographic data
    Enabled live connection in Power BI to reflect real-time metrics
----------------------------------------------------------------------------------------------------------------------------------

🧠 What I Learned:
    Hands-on experience with Power BI data modeling, DAX, and real-time reporting
    How to structure large data projects with multiple fact and dimension tables
    Applied SQL transformations and best practices for dashboard performance optimization
----------------------------------------------------------------------------------------------------------------------------------

📬 Contact:
📧 Email: rishabh.tiw1020@gmail.com


