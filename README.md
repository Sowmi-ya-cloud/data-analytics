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

Used the following functions to understand the distribution of numerical columns such as Price, Quantity, and Total Sales:

Mean: df.mean()
Median: df.median()
Mode: df.mode()
Standard Deviation: df.std()

These measures helped identify the average sales values and understand the spread of the data.

✅ Trend Analysis
Converted the Date column using pd.to_datetime().
Used groupby('Date') to analyze how total sales changed over time.
Observed monthly sales patterns and peak sales periods.

✅ Category Analysis
Grouped the data by Category to determine which categories generated the highest sales.
Compared the contribution of each category to overall revenue.

✅ Product Analysis
Analyzed sales performance of different products.
Identified top-selling products based on total sales and quantity sold.

✅ Location Analysis
Grouped data by Location to compare regional sales performance.
Identified locations contributing the highest revenue.

✅ Payment Method Analysis
Examined the distribution of various payment methods.
Determined the most frequently used payment method among customers.

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

  •	Bar chart: Shows Confirmed cases by Country
  •	Line graph: Shows Spread trend by month
  •	Pie chart: Shows Death share by regions
  •	KPI Cards: Shows Total Confirmed, Total Recovered, Total Deaths.

 <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/f7cb054f-04f1-4461-8de7-21d0f6b751a2" />

## 📊 Results(screenshots) & Insights

### ✅ Screenshots

### Libraries imported

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7ae08692-52d4-4db8-bba5-337ad76ef06f" />

### Inspect data

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/c703782c-dabf-4537-801f-e9787a3c2b37" />

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/2cf2203a-222b-4ead-8e77-d1e8da9dfd00" />

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/074e2d0c-52ee-4be1-b915-bd3ea2217abe" />

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/6b44b088-d5f9-4f67-a2ee-d1edabfe7bf7" />

### Checked duplicates

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/adeec178-6758-4c37-ad06-b9e0a67224dd" />

### Finding missing values

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/f64ef1e6-9f33-469e-954a-e43b34329f35" />

### Replaced column name

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/9896a0c5-8efd-49de-8c6c-f5eb5c94d4b6" />

### EDA

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/73622327-8d2f-4f50-ac4f-5f8c8ad6d76a" />

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/db514425-ea2f-4d41-bc84-40873aaa8ab0" />

### Trend Analysis

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/c3a7996e-7263-4336-ac71-4dca2d54f5e3" />


✅ Insights

•	Median deaths are just 2, but average is around 884. So, most regions had very low deaths.

•	The dataset covers many different global regions because the latitude and longitude values spread widely.

•	The most commonly repeated region in the dataset belongs to China, which makes sense because initial COVID reporting started there.

•	Confirmed vs Deaths (0.91) - strong positive relationship. More cases resulted in more deaths.

## 📝 Challenges Faced

✅ Understanding Correlation Meaning

•	At first, it was confusing to interpret the correlation values.

•	I took time to learn that higher positive values mean strong relationships.
     
✅ Power BI dashboard creation:

•	I faced some confusion while designing the dashboard, especially in choosing the right colours and deciding where each chart should be placed.

•	To overcome this, I looked at a few sample dashboards. This helped me understand how to arrange the visuals in a clean and logical flow.

## ✍️ Reflection

•	Understood cloud storage and dataset versioning using AWS S3.
  
•	Became confident with Pandas, NumPy, Matplotlib and Seaborn.
  
•	Learned how to create a clean and meaningful analytics Power BI dashboard.






