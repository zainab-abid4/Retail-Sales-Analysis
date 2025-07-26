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
```
![Alt Text](https://github.com/zainab-abid4/Retail-Sales-Analysis/blob/868a78d52a0bcfd56c6cf334a11258567c4cf48c/MONTHLY%20SALES.PNG)


**Best-Selling Products**
```python
top_products = merged_df.groupby('product_name')['total'].sum().sort_values(ascending=False).head(10)
sns.set_style("whitegrid")
colors = sns.color_palette("Blues_d", len(top_products))
plt.figure(figsize=(10,6))
top_products.plot(kind='barh', color=colors)
plt.title("Top 10 Best-Selling Products", fontsize=12, fontweight='bold')
plt.xlabel("Total Sales (Rp)")
plt.gca().invert_yaxis()
plt.tight_layout()
plt.show()
```
![Alt Text](https://github.com/zainab-abid4/Retail-Sales-Analysis/blob/868a78d52a0bcfd56c6cf334a11258567c4cf48c/BEST%20SELLING.PNG)


**Regional Sales by City** 
```python
region_sales = merged_df.groupby('city_y')['total'].sum().sort_values(ascending=False)
sns.set_style("whitegrid")
colors = sns.color_palette("Blues_r", len(region_sales))  # Reverse blue scale for visual appeal
plt.figure(figsize=(10,6))
region_sales.plot(kind='bar', color=colors)
plt.title("Sales by Regions",fontsize=12,fontweight='bold')
plt.ylabel("Total Sales (Rp)")
plt.xlabel("City")
plt.xticks(rotation=45)
plt.legend(loc='upper right')
plt.tight_layout()
plt.show()
```
![Alt Text](https://github.com/zainab-abid4/Retail-Sales-Analysis/blob/868a78d52a0bcfd56c6cf334a11258567c4cf48c/SALES%20BY%20REGION.PNG)

**Customer Segmentation by Spend**
```python
customer_spend = merged_df.groupby('customer_id')['total'].sum()
# Define segments (top 20%, mid 60%, bottom 20%)
high = customer_spend.quantile(0.80)
low = customer_spend.quantile(0.20)
segments = customer_spend.apply(
    lambda x: 'High-Value' if x >= high else ('Low-Value' if x <= low else 'Mid-Value')
)
sns.set_style("whitegrid")
colors = ['#1f77b4', '#6baed6', '#d9d9d9']
segment_counts = segments.value_counts()
plt.figure(figsize=(6,6))
segment_counts.plot(kind='bar', color=colors)
plt.title("Customer Segments by Spend",fontsize=12, fontweight='bold')
plt.ylabel("Number of Customers")
plt.xticks(rotation=0)
plt.tight_layout()
plt.legend()
plt.show()
```
![Alt Text](https://github.com/zainab-abid4/Retail-Sales-Analysis/blob/868a78d52a0bcfd56c6cf334a11258567c4cf48c/CUSTOMER%20SPEND.PNG)


**Top 10 products by sales**
```python
top_products = merged_df.groupby('product_name')['total'].sum().sort_values(ascending=False).head(10)

colors = plt.cm.Pastel1(range(10))  # Use a pastel color palette
explode = [0.05] * 10               # Slight explode on all slices for style

plt.figure(figsize=(8,8))
plt.pie(
    top_products,
    labels=top_products.index,
    autopct='%1.1f%%',
    startangle=140,
    shadow=True,
    colors=colors,
    explode=explode,
    wedgeprops={'edgecolor': 'black', 'linewidth': 1.2},  # Border around slices
    textprops={'fontsize': 12}
)

plt.title("Top 10 Products by Total Sales", fontsize=12, fontweight='bold')
plt.axis('equal')   # Keep the pie circular
plt.tight_layout()
plt.show()
```
![Alt Text](https://github.com/zainab-abid4/Retail-Sales-Analysis/blob/868a78d52a0bcfd56c6cf334a11258567c4cf48c/TOP%2010%20PRODUCTS.PNG)


## Key Insights

1. Sales peak during specific months, suggesting seasonal trends
2. A small number of products drive the majority of revenue  
3. Big cities dominate sales, highlighting regional gaps  
4. Top 20% of customers are high-value spenders  
5. Product category performance varies significantly

