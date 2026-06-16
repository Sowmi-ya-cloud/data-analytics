## 📌 Project Title & Objective

**Title:** Mobile Specifications & Sales Performance Dashboard

**Objective:** The objective of this project is to analyze mobile phone specifications and sales performance across brands like Realme, Apple, Xiaomi, Poco, and Samsung — identifying revenue trends, popular specifications, and market distribution using an interactive Power BI dashboard.

## 🏗️ Architecture Diagram

                     Mobile Shop Dataset

                             ↓

                    Data Cleaning (Python)

                             ↓

                 Exploratory Data Analysis (EDA)

                             ↓

                      Power BI Dashboard

                             ↓

                      Business Insights

## 📂 Dataset Overview

This project uses **4 separate CSV tables**:

| Table | Key Columns |
|-------|-------------|
| `mobile_info.csv` | brand_name, RAM, ROM, total_memory |
| `camera.csv` | num_rear_camera, num_front_camera, battery_capacity |
| `display.csv` | display_size, screen_size |
| `sales.csv` | sales_price, discount_percent, sales, revenue, final_price |

## ⚙ Implementation steps

### Step 1: Dataset Collection & Upload

- Selected **Mobile Shop dataset** from Kaggle (4 tables)
- **Purpose:**
  - Analyze mobile specifications across brands
  - Identify sales trends and discount impact on revenue
  - Monitor KPIs like total revenue, ratings, and brand performance
- Uploaded dataset using Google Colab

```python
from google.colab import files
uploaded = files.upload()

import pandas as pd
import numpy as np

# Load all 4 tables
mobile_info = pd.read_csv("mobile_info.csv")    # mobile info table
camera      = pd.read_csv("camera.csv")         # camera specs table
display     = pd.read_csv("display.csv")        # display table
sales       = pd.read_csv("sales.csv")          # sales table

mobile_info.head()                              # Inspect data
```

---

<img width="800" height="400" alt="WhatsApp Image 2026-06-16 at 5 13 34 PM" src="https://github.com/user-attachments/assets/32a26372-48b2-4a4d-9c93-80cf85da7549" />

### Step 2: Data Cleaning

✅ **Handled Missing Values** — Checked all 4 tables for null values

```python
mobile_info.isnull().sum()
camera.isnull().sum()
display.isnull().sum()
sales.isnull().sum()
```
<img width="800" height="400" alt="WhatsApp Image 2026-06-16 at 5 14 17 PM" src="https://github.com/user-attachments/assets/5cfe5706-e3c7-4ec8-a233-e899883ba027" />

✅ **Removed Duplicate Values** — Verified no repeated rows across all tables

```python
mobile_info.duplicated().sum()
camera.duplicated().sum()
display.duplicated().sum()
sales.duplicated().sum()
```

---

<img width="400" height="400" alt="WhatsApp Image 2026-06-16 at 5 14 49 PM" src="https://github.com/user-attachments/assets/e273aa10-296f-4de5-9c33-10571cf04141" />

### Step 3: Exploratory Data Analysis (EDA)

✅ **Central Tendency — Mean & Median**

Calculated mean and median for key numerical columns across all tables:

```python
mean_median = {
    "mobile_info": mobile_info[['RAM','ROM']].agg(['mean','median']),
    "camera": camera[['num_rear_camera','num_front_camera','battery_capacity']].agg(['mean','median']),
    "display": display[['display_size']].agg(['mean','median']),
    "sales": sales[['sales_price','discount_percent','sales']].agg(['mean','median'])
}
```
<img width="800" height="400" alt="WhatsApp Image 2026-06-16 at 5 15 42 PM" src="https://github.com/user-attachments/assets/1a96eda7-b3a1-45a5-be80-da7e891dcafd" />

✅ **Mode Analysis**

```python
mode = {
    "mobile_info": mobile_info[['brand_name']].mode(),
    "camera": camera[['num_rear_camera']].mode()
}
```
<img width="800" height="484" alt="WhatsApp Image 2026-06-16 at 5 16 05 PM" src="https://github.com/user-attachments/assets/cb222f58-1950-4dfe-9c9a-7f3783c84179" />

✅ **Data Spread — Std Dev, Variance, Min, Max, Range**

Analyzed spread of RAM, ROM, battery capacity, display size, and sales price across all tables.

<img width="800" height="450" alt="WhatsApp Image 2026-06-16 at 5 23 34 PM" src="https://github.com/user-attachments/assets/1155fa46-bebf-4fa0-aaea-637e4528ecf8" />


✅ **Correlation & Relationship Analysis**

```python
relationships = {
    "sales": sales[['sales_price','discount_percent','sales']].corr()
}

# Heatmap visualization
import seaborn as sns
import matplotlib.pyplot as plt

sns.heatmap(sales[['sales_price','discount_percent','sales']].corr(),
            annot=True, cmap='coolwarm')
```
<img width="800" height="400" alt="WhatsApp Image 2026-06-16 at 5 21 03 PM" src="https://github.com/user-attachments/assets/94cd463a-b02a-4b96-bdcd-75d825c445de" />

✅ **Brand & Screen Size Distribution**

```python
print(mobile_info['brand_name'].value_counts())
print(display['screen_size'].value_counts())
```

---

### Step 4: Visualization Using Power BI

The dashboard contains:

| Visual | Description |
|--------|-------------|
| 📊 Bar Chart | Total Revenue by Brand |
| 📈 Line Chart | Sales Revenue by Screen Size |
| 🍩 Donut Chart | Mobile Models Count by Brand |
| 🗺️ Tree Map | RAM vs Total Mobiles |
| 📊 Bar Chart | Number of Mobiles by Base Color |
| 🔢 KPI Cards | Total Revenue (200.55M) & Max Rating (4.60) |

---

<img width="800" height="450" alt="WhatsApp Image 2026-06-16 at 5 11 53 PM" src="https://github.com/user-attachments/assets/57149796-ee6d-4cd5-bcfa-b2720835f418" />


## 📊 Results & Insights

✅ **Insights**

- 📌 **Realme** recorded the highest total revenue among all brands
- 💾 Higher **RAM + ROM** combinations led to higher sales prices
- 📷 Most mobiles had **2 rear cameras** as the most common configuration
- 💰 Discount percentage had a **negative correlation** with sales price — higher discounts on lower-priced phones
- 📐 **Large screen size** mobiles contributed the most to sales revenue
- ⭐ Maximum customer rating achieved was **4.60**
- 💵 Total revenue across all brands reached **200.55M**

---

## 📝 Challenges Faced

✅ **Working with Multiple Tables**

- Managing 4 separate CSV files simultaneously was initially complex
- Learned to apply cleaning and EDA operations consistently across all tables

✅ **Feature Engineering**

- Creating meaningful derived columns like `final_price`, `total_memory`, and `revenue` required careful formula design
- Ensured no data leakage by applying discount logic correctly

✅ **Power BI Dashboard Design**

- Faced difficulty choosing suitable chart types for specification-based data
- Referred to sample dashboards to improve layout, color theme, and visual arrangement

---

## ✍️ Reflection

- 🐍 Strengthened multi-table data cleaning and preprocessing using **Pandas and NumPy**
- 📐 Improved understanding of **descriptive statistics** — mean, median, mode, std dev, variance
- 🔗 Learned to analyze **correlations** across numerical features using heatmaps
- 🛠️ Practiced **feature engineering** to create new meaningful columns
- 📊 Developed an interactive **Power BI dashboard** for visualizing mobile KPIs and trends
- 💡 Gained end-to-end experience from raw data cleaning to business insight generation


