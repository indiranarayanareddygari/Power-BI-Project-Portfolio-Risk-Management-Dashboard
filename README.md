# Power-BI-Project-Portfolio-Risk-Management-Dashboard

📁 Project Overview
This Power BI project focuses on Portfolio Risk Management using real-world stock data. The goal is to analyze the performance, volatility, and correlation of multiple stocks to derive meaningful investment insights. The dashboard helps investors monitor portfolio metrics and identify high-performing and underperforming assets.
--
# 📌 Objectives 

Track portfolio average return and volatility

Identify best and worst performing stocks

Analyze volatility by stock

Visualize daily returns trend

Examine return correlations across stocks

Explore risk-return trade-offs through scatter plots

Enable deep filtering by year, stock, and month

--

📂 Dataset
Source: https://www.kaggle.com/datasets/ankurnapa/stock-portfolio-financial-risk-analytics

Choose any stock

Timeframe: 2010–2020

Stocks Used in This Dashboard: AMZN, GOOG, IBM, FB, LUV, SP500

--
# ✅ Project Steps
1. Data Loading
Imported multiple CSV stock files into Power BI
Merged into a single combined table using Power Query

2. Data Cleaning (Power Query)
Parsed Date column
Ensured data type consistency
Removed null/duplicate values

3. Data Modeling
Created relationships where needed
Built DAX calculated columns and measures:

🧮 DAX Measures:

Daily Return (%) = ([Close] - [Open]) / [Open] * 100
Avg Return (%) = AVERAGE('Table'[Daily Return (%)])
Volatility (%) = STDEV.P('Table'[Daily Return (%)])
Portfolio Avg Return (%) = AVERAGEX(VALUES('Table'[Stock]), [Avg Return (%)])
Portfolio Volatility (%) = AVERAGEX(VALUES('Table'[Stock]), [Volatility (%)])

🔎 Best/Worst Stock (using DAX):
Best Performing Stock = 
    CALCULATE(MAX('Table'[Stock]), 
    FILTER('Table', [Avg Return (%)] = MAXX(ALL('Table'), [Avg Return (%)])))

Worst Performing Stock = 
    CALCULATE(MIN('Table'[Stock]), 
    FILTER('Table', [Avg Return (%)] = MINX(ALL('Table'), [Avg Return (%)])))
    
# 📊 Dashboard Visuals
# Visual	Description
KPI Cards	Portfolio Avg Return (%), Portfolio Volatility (%), Best/Worst Stock
Volatility by Stock	Bar chart showing risk exposure of each stock
Daily Returns Trend	Multi-line chart comparing stock returns over time
Correlation Heatmap	Python-based heatmap to show correlation among stocks
Risk vs Return Scatter Plot	Visualizing trade-off between average return and volatility
Stock & Year Slicers	Filter dashboard by stock and time
Monthly Returns Matrix	Matrix showing average monthly return per stock

🐍 Python Visual – Correlation Heatmap
Python code 
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

dataset['Date'] = pd.to_datetime(dataset['Date'], errors='coerce')
pivot_df = dataset.pivot(index='Date', columns='Stock', values='Daily Return (%)').dropna()
corr_matrix = pivot_df.corr()

fig, ax = plt.subplots(figsize=(8,6))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', linewidths=0.5, ax=ax)
ax.set_title('Stock Return Correlation Heatmap')
plt.tight_layout()
plt.show() in Power BI Python visuals.

🔧 Advanced Features Implemented
🔄 Sync Slicers for unified filtering across visuals
📅 Dynamic filtering by Year, Stock, and Month
📈 Matrix filtering for analyzing performance in a specific month (e.g., April)
🔎 Performance Analyzer to monitor and optimize visual load times

🧠 Skills Showcased
Power Query (Data Cleaning & Merging)
Data Modeling in Power BI
DAX Calculations and Aggregations
Custom Visuals using Python
Interactive Slicers
Report Design Best Practices

----
## ✍️ Author
**Indira 

(https://www.linkedin.com/in/indira-narayanareddygari-analyst061294/)

**Data Analyst | Power BI Developer | SQL & Excel Specialist | Python Enthusiast**

## 📸 Screenshot ![Dashboard](https://github.com/user-attachments/assets/96f62c3f-22af-4d17-a8b5-4235e620a8df)

## Dashboard Link :  https://app.powerbi.com/groups/me/reports/c63c699e-df9e-4bc4-825c-c4d99e7cfcba/b6b3137756f8233292be?experience=power-bi
