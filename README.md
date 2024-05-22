# CREDIT CARD FINANCIAL DASHBOARD

### PROJECT OVERVIEW

The primary goal of this project is to develop a comprehensive, real-time dashboard using Power BI that offers stakeholders insightful and actionable data regarding key performance metrics and trends in credit card operations. This will enable effective monitoring, analysis, and strategic decision-making.

### DATA SOURCES
The primary data used for this analysis is the "credit_card.csv" and "cust.csv" files. These datasets enable comprehensive analysis and visualization of credit card operations and customer insights.

### TOOLS
- Excel - Data Cleaning
- SQL database and Server - Importing Data to SQL database
- PowerBI - Creating Interactive Reports

### DATA CLEANING AND PREPARATION
In the initial data preparation phase, we performed the following tasks:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.

### EXPLORATORY DATA ANALYSIS

EDA involves exploring the financial data to answer key questions, such as :
1. What are the weekly revenue trends across different card types?
2. How does customer satisfaction vary by income group and gender?
3. Which states have the highest number of active credit card users?
4. What is the distribution of transactions by marital status and salary count?
5. How do transaction volumes differ between male and female customers?


### DAX QUERIES

AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
 )
IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)

week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))) 
Previous_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

 

### KEY FEATURES AND FUNCTIONALITY

1. Interactive Weekly Report
- Both dashboards provide real-time updates and insights on a weekly basis, ensuring stakeholders have the most current information available.

2. Filter Components :
- Gender-based filters (Male and Female) to analyze data by gender demographics.
- Income-based filters to segment data by different income groups.
- Card type filters to segregate data based on the type of credit card used.
- Quarter analysis to compare metrics across different quarters.

3. Interactive APIs
- Integration of APIs to fetch and display real-time data dynamically, ensuring the dashboards are always up-to-date with the latest information.

4. Column Charts and Comparative Analysis
- Utilization of column charts to compare different revenue metrics, providing a clear visual representation of performance trends and differences.

  ### Dashboard Breakdown

## Credit Card Customer Report

- ## Revenue vs. Gender Analysis
- Weekly performance metrics segmented by gender, providing insights into revenue generation patterns across male and female customers.

- ## Customer Satisfaction Score (CSS)
- Measurement of customer satisfaction on a weekly basis, helping to gauge customer sentiment and identify areas for improvement.

- ## Demographic Metrics
- Analysis of metrics such as marital status and salary count groups to understand the demographic composition of the customer base.

- ## Top Five States
- Highlighting the top five states with the highest number of customers, aiding in geographic targeting and resource allocation.


  ### CREDIT CARD TRANSACTION REPORT

- ## Transaction Metrics
-Detailed insights into credit card transactions, including volume, value, and frequency, comparative analysis of transaction data across different time periods and customer segments.

 - ## Revenue Metrics
  Examination of revenue generated from transactions, with breakdowns by card type, income group, and gender.
  
- ## Quarterly Analysis
  Trends and patterns in transaction data over quarterly periods, identifying seasonal or periodic variations.

  ### Benefits to Stakeholders
  
- ## Real-Time Insights
Immediate access to up-to-date information, allowing for quick and informed decision-making.

- ## Enhanced Analysis
Comprehensive filtering and comparison capabilities enable detailed and nuanced analysis of credit card operations.

- ## Performance Monitoring
Continuous tracking of key performance indicators (KPIs) ensures stakeholders can monitor the health and performance of credit card programs.

- ## Strategic Planning
Insights derived from the dashboards support strategic planning and operational adjustments to optimize performance and customer satisfaction.

### Implementation and Maintenance

- ## Data Integration
Ensure seamless integration with existing data sources and APIs to maintain real-time data updates.

- ## User Training
Provide training sessions for stakeholders to effectively use and interpret the dashboards.

- ## Continuous Improvement
Regular updates and enhancements based on user feedback and evolving business needs to keep the dashboards relevant and effective.


### PROJECT INSIGHTS - WEEK 53 ( 31st DEC)

WoW Change : 
- Revenue increased by 24.4 %
- Total Transaction Amt & Count increased by 2.0M % & 100%
- Customer count increased by xx%

Overview YTD:
- Overall revenue is 57.7M
- Total interest is 8.1M
- Total transaction amount is 46.5M
- Male customers are contributing more in revenue 32M, female 26M
- Average Age is 46
- Blue & Silver credit card are contributing to 93.5% of overall transactions
- TX, NY & CA is contributing to 72.85%
- Overall Activation rate is 57.44%
- Overall Delinquent rate is 6.05%
- Highest category in delinquent rate is from "self-employed" which is 14.88%


  ## CONCLUSION
  
The comprehensive credit card weekly dashboard project aims to provide stakeholders with powerful tools to monitor, analyze, and optimize credit card operations. By leveraging the capabilities of Power BI, this project delivers real-time insights, detailed analytics, and interactive visualizations that drive better decision-making and strategic planning.
