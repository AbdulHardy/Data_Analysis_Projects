# 📉 E‑Commerce Customer Churn Analysis

## 📌 Project Overview

Customer churn is a major challenge for e‑commerce businesses. This project performs **behavior‑based churn analysis** using transactional data to identify customers who are likely to stop purchasing and to uncover the key drivers of churn.

This is a **portfolio‑ready, end‑to‑end data analysis project** covering:

* Data loading & cleaning
* Feature engineering
* Churn definition
* Exploratory data analysis (EDA)
* Visualizations
* Business insights & recommendations

---

## 🧰 Tools & Technologies

* **Python**
* **Pandas** – data manipulation
* **NumPy** – numerical operations
* **Matplotlib & Seaborn** – data visualization
* **Google Colab** – development environment

---

## 📂 Dataset Description

The dataset contains transactional e‑commerce purchase records with the following attributes:

| Column            | Description                 |
| ----------------- | --------------------------- |
| User_ID           | Unique customer identifier  |
| Product_ID        | Unique product identifier   |
| Category          | Product category            |
| Price (Rs.)       | Original product price      |
| Discount (%)      | Discount percentage applied |
| Final_Price (Rs.) | Price after discount        |
| Payment_Method    | Payment type used           |
| Purchase_Date     | Date of purchase            |

---

## 🧹 Step 1: Data Loading

```python
import pandas as pd
import numpy as np

df = pd.read_csv("ecommerce_dataset.csv")
```

**Explanation:**

* Loaded raw transactional data into a Pandas DataFrame for analysis.

---

## 🧼 Step 2: Column Name Cleaning

```python
df.columns = (
    df.columns
    .str.strip()
    .str.lower()
    .str.replace(' ', '_')
    .str.replace('.', '', regex=False)
)

# Fix column typo
df.rename(columns={'final_pricers': 'final_price_rs'}, inplace=True)
```

**Explanation:**

* Standardized column names for consistency
* Removed special characters
* Corrected naming inconsistencies to avoid aggregation errors

---

## 🔍 Step 3: Data Quality Checks

```python
df.info()
df.isnull().sum()
```

**Explanation:**

* Checked data types and missing values to ensure data integrity

---

## 🛠️ Step 4: Data Type Fixing

```python
numeric_cols = ['price_rs', 'discount_pct', 'final_price_rs']
for col in numeric_cols:
    df[col] = pd.to_numeric(df[col], errors='coerce')

df['purchase_date'] = pd.to_datetime(df['purchase_date'], errors='coerce')

df.dropna(inplace=True)
```

**Explanation:**

* Converted numerical and date columns to correct data types
* Removed rows with critical missing values

---

## 🧾 Step 5: Remove Duplicates

```python
df.drop_duplicates(inplace=True)
```

**Explanation:**

* Ensured no duplicate transactions distort analysis

---

## 👥 Step 6: Customer‑Level Feature Engineering

```python
customer_df = df.groupby('user_id').agg(
    first_purchase=('purchase_date', 'min'),
    last_purchase=('purchase_date', 'max'),
    total_orders=('product_id', 'count'),
    total_spent=('final_price_rs', 'sum'),
    avg_order_value=('final_price_rs', 'mean'),
    avg_discount=('discount_pct', 'mean')
).reset_index()
```

**Explanation:**

* Aggregated transactional data into customer‑level features required for churn analysis

---

## ⏰ Step 7: Churn Definition

**Business Rule:**

> A customer is considered *churned* if they have not made a purchase in the last **60 days**.

```python
analysis_date = df['purchase_date'].max()
churn_threshold = 60

customer_df['days_since_last_purchase'] = (
    analysis_date - customer_df['last_purchase']
).dt.days

customer_df['churn'] = customer_df['days_since_last_purchase'] > churn_threshold
```

**Explanation:**

* Created a churn flag based on customer inactivity
* This represents behavior‑based churn common in e‑commerce businesses

---

## 📊 Step 8: Churn Rate Calculation

```python
churn_rate = customer_df['churn'].mean() * 100
churn_rate
```

**Explanation:**

* Calculated overall churn percentage to measure retention risk

---

## 📈 Step 9: Churn Analysis & Visualizations

### 🔹 Churn Distribution

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(x='churn', data=customer_df)
plt.title('Customer Churn Distribution')
plt.show()
```
<img width="852" height="778" alt="customer Churn distribution" src="https://github.com/user-attachments/assets/2346c13f-0169-4dcc-b212-5ad04e161424" />

### 🔹 Orders vs Churn

```python
sns.boxplot(x='churn', y='total_orders', data=customer_df)
plt.title('Total Orders vs Churn')
plt.show()
```
<img width="802" height="704" alt="Total orders vs Churn" src="https://github.com/user-attachments/assets/5575c4ba-cf73-4477-895f-fb77a1df0e74" />

### 🔹 Spending vs Churn

```python
sns.boxplot(x='churn', y='total_spent', data=customer_df)
plt.title('Total Spending vs Churn')
plt.show()
```
<img width="794" height="703" alt="total spending vs churn" src="https://github.com/user-attachments/assets/c02a90e2-82c6-47d6-b577-3569589caf23" />


### 🔹 Discount Dependency

```python
sns.boxplot(x='churn', y='avg_discount', data=customer_df)
plt.title('Average Discount vs Churn')
plt.show()
```
<img width="779" height="693" alt="Average Discount vs Churn" src="https://github.com/user-attachments/assets/c2c31a9b-50e5-400a-a1ea-46417dcda8f0" />

### 🔹 Inactivity Pattern

```python
sns.histplot(
    data=customer_df,
    x='days_since_last_purchase',
    hue='churn',
    bins=30
)
plt.title('Days Since Last Purchase vs Churn')
plt.show()
```
<img width="744" height="768" alt="Day since last day purchase vs churn" src="https://github.com/user-attachments/assets/7252c4f6-3861-4e75-981b-30677081839e" />

---

## 🧠 Key Insights

* Customers with **low purchase frequency** are more likely to churn
* **High‑spending customers** show stronger retention
* Heavy **discount dependency** correlates with higher churn
* Inactivity beyond **45–60 days** is a strong churn indicator

---

## 🎯 Business Recommendations

* Launch **win‑back campaigns** after 45 days of inactivity
* Introduce **loyalty programs** for repeat buyers
* Reduce over‑reliance on discounts by promoting value‑based offers
* Prioritize retention strategies for **high‑value customers**

---

