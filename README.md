# Retail-Sales-Analysis
**Project Title**: Retail Sales Analysis   

## Project Overview
This project analyzes Indonesian retail sales data to uncover insights into product performance, customer behavior, regional trends, and time-based sales patterns. Data from customers, products, transactions, and transaction details was merged and visualized using Python.

## Dataset 
The dataset used in ths project simulates customer transactions for various iPhone models in Indonesia, capturing key aspects of consumer behavior, product preferences, and sales dynamics in the local market. It includes information about sales transactions, store details, and product information..This dataset is a available on Kaggle. 

## OBJECTIVES

1. **Set up a retail sales dataset**: Create and populate a retail sales database with the provided sales data.
2. **Data Cleaning**: Clean and merge datasets into a unified format.
3. **Exploratory Data Analysis (EDA)**: Perform basic exploratory data analysis to understand the dataset.
4. **Data Visualization**: Analyze sales trends, top products, and regional performance.
5. **Business Analysis**: Derive insights from the sales data.

## DATA VISUALIZATIONS
**Monthly Sales Trend** 
``` python
monthly_sales = merged_df.groupby('Month')['total'].sum()
sns.set_style("whitegrid")
plt.figure(figsize=(8,6))
monthly_sales.plot(marker='o')
plt.title("Monthly Sales Trend", fontsize=16, fontweight='bold')
plt.xlabel("Month")
plt.ylabel("Total Sales (Rp)")
plt.xticks(rotation=45, fontsize=10)
plt.yticks(fontsize=10)
plt.grid(True, linestyle='--', alpha=0.6)
plt.legend()

plt.tight_layout()
plt.show()


**Top 10 Best-Selling Products**  
**Regional Sales by City**  
**Product Category Share**  
**Customer Segmentation by Spend**

## 🧠 Key Insights

1. Sales peak during specific months, suggesting seasonal trends
2. A small number of products drive the majority of revenue  
3. Big cities dominate sales, highlighting regional gaps  
4. Top 20% of customers are high-value spenders  
5. Product category performance varies significantly

