# Data Analytics Project: Sales Performance Analysis Dashboard

## 📌 Project Title & Objective

**Title:** Sales Performance Analysis Dashboard

**Objective:** To analyze sales data and identify key trends, top-performing products, regional performance, and profitability using Python, SQL, and Power BI. The goal is to transform raw sales data into actionable business insights through interactive dashboards.

## 🏗️ Architecture Diagram

Sales Dataset
        ↓
Data Cleaning
        ↓
Exploratory Data Analysis (EDA)
        ↓
SQL Analysis
        ↓
Power BI Dashboard
        ↓
Business Insights

## ⚙ Implementation steps

### Step 1: Dataset Collection & Upload

 •	Selected Amazon sales dataset from Kaggle.

 •Purpose:
         • Analyze sales trends and profitability.
         • Identify top-performing products and regions.
         • Monitor key business KPIs.
         • Loaded the dataset using Python libraries.
 
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/5d3f0b8b-2057-4734-a004-4448dcb32b6c" />

```bash
Python code: 

from google.colab import files                           # Upload dataset 
uploaded = files.upload()

import pandas as pd                                      # Import libraries 
import numpy as np

df = pd.read_csv("amazon_sales_data.csv")                # Load dataset 

df.head()                                                # Inspect data
df.info()
df.shape`
df.describe()
```

### Step 2: Data Cleaning

✅ Removed Duplicate values

Used the drop_duplicates() function to ensure that all rows in the dataset were unique and no repeated entries were present.
 
✅ Handled Missing Values

Checked for missing values using isnull().sum().
Used dropna() to remove province/state column. (to remove unnecessary null rows).

```bash
Python code:
df.duplicated().sum()                          # checking duplicates

df.drop_duplicates(inplace=True)

df.isnull().sum()                              # checking missing values
```

### Step 3: Exploratory Data Analysis (EDA)

✅ Calculated Statistical Measures

•      Used the following functions to understand the distribution of numerical columns such as Price, Quantity, and Total Sales:

          Mean: df.mean()

          Median: df.median()

          Mode: df.mode()

          Standard Deviation: df.std()

•      These measures helped identify the average sales values and understand the spread of the data.

✅ Trend Analysis

•     Converted the Date column using pd.to_datetime().

•     Used groupby('Date') to analyze how total sales changed over time.

•     Observed monthly sales patterns and peak sales periods.

✅ Category Analysis

•      Grouped the data by Category to determine which categories generated the highest sales.

•      Compared the contribution of each category to overall revenue.

✅ Product Analysis

•      Analyzed sales performance of different products.

•      Identified top-selling products based on total sales and quantity sold.

✅ Location Analysis

•      Grouped data by Location to compare regional sales performance.

•      Identified locations contributing the highest revenue.

✅ Payment Method Analysis

•      Examined the distribution of various payment methods.

•      Determined the most frequently used payment method among customers.

✅ Order Status Analysis

       Analyzed the status of orders to understand the proportion of completed, pending, and cancelled orders.

```bash
Python code:
# Convert date column
df['Date'] = pd.to_datetime(df['Date'])

# Trend Analysis
sales_trend = df.groupby('Date')['Total Sales'].sum()

# Category Analysis
category_sales = df.groupby('Category')['Total Sales'].sum()

# Product Analysis
product_sales = df.groupby('Product')['Total Sales'].sum()

# Location Analysis
location_sales = df.groupby('Location')['Total Sales'].sum()

# Payment Method Analysis
payment_analysis = df.groupby('Payment Method')['Total Sales'].sum()

# Status Analysis
status_count = df['Status'].value_counts()
```
### Step 4: Visualization Using Power BI

The dashboard contains:

  •	Bar chart: Shows Total sales by Category
  •	Line Chart: Shows Total sales by month
  •	Pie chart: Shows Total sales by Product
  •	KPI Cards: Shows of total sales and sales target by Date.
  •     Tree Map : Shows sum of quantity by customer name.

<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/5c1ab641-8ea7-4ad4-bdd1-5d36384b13d5" />

<img width="1366" height="672" alt="WhatsApp Image 2026-06-16 at 4 47 49 PM" src="https://github.com/user-attachments/assets/1eceece3-b216-4f9c-a124-322c3848df49" />


✅ Insights

•	Electronics category recorded the highest sales.

•       Some products performed better than others in terms of revenue.

•       Sales varied across different locations.

•       Most customers preferred online payment methods.

•       The majority of orders were successfully completed.

•       Sales showed changes over time, indicating different customer demand patterns.

•       Higher quantities sold resulted in higher total sales.

## 📝 Challenges Faced

✅ Understanding GroupBy Operations

• Initially, it was challenging to summarize data using groupby functions.

• Practiced aggregation techniques to better understand trends and patterns.

✅ Power BI Dashboard Creation

• Faced difficulty in selecting suitable charts and arranging visuals.

• Referred to sample dashboards to improve dashboard design and readability.

## ✍️ Reflection

•      Strengthened data cleaning and preprocessing skills using Pandas and NumPy.

•      Improved understanding of exploratory data analysis techniques.

•      Learned to use SQL queries for extracting business insights.

•      Developed interactive Power BI dashboards for visualizing KPIs and trends.

•      Gained practical experience in transforming raw sales data into meaningful business insights.







