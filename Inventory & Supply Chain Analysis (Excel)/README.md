# Inventory & Supply Chain Performance Analysis

## 📌 Project Objective
The objective of this project is to analyze inventory and supply chain performance
using Excel, identify stock risks, understand warehouse and supplier performance,
and build an interactive dashboard to support data-driven business decisions.

This project was built as a **core Excel analytics project** for a Data Analyst portfolio.

---

## 📊 Dataset Overview
- Records: ~30,000 rows
- Domain: Inventory & Supply Chain
- Data Type: Transaction-level inventory data

Key fields include:
- Product Name & Category
- Warehouse
- Supplier
- Stock In & Stock Out
- Unit Cost
- Inventory Value
### 📂 Dataset
You can download the cleaned dataset here:
[Download Dataset](inventory_supply_chain_30k.xlsx)(https://raw.githubusercontent.com/AbdulHardy/Data_Analysis_Projects/main/Inventory%20%26%20Supply%20Chain%20Analysis%20(Excel)/inventory_supply_chain_30k.xlsx)


---

 ## 🛠 Tools & Skills Used
- Microsoft Excel
- Power Query (ETL & Data Cleaning)
- Pivot Tables
- KPI Design
- Excel Dashboard Design

---

## 🔄 Step-by-Step Project Workflow

### 1️⃣ Data Loading & Cleaning (Power Query)
- Loaded raw inventory data into Power Query
- Verified data quality:
  - No duplicate records
  - No invalid values
  - No empty rows
- Handled missing values logically:
  - Unit Cost kept as **null** where applicable
- Ensured correct data types for all columns

---

### 2️⃣ Feature Engineering (New Columns Created)
Created business-driven calculated columns using Power Query:

- **Net Stock**

- **Inventory Risk**
- High Risk → Net Stock ≤ 0 or Unit Cost is null
- Medium Risk → Net Stock ≤ 10
- Low Risk → Net Stock > 10

- **Stock Movement Type**
- Inbound
- Outbound
- No Movement

These columns enabled meaningful KPI analysis.

---

### 3️⃣ KPI Development (Pivot Tables)
Built KPIs using Pivot Tables to answer business questions such as:

- What is the total inventory value?
- Which products are at high inventory risk?
- Which warehouse holds the highest inventory value?
- Which suppliers contribute most to inventory?
- Stock In vs Stock Out performance
- Category-wise and product-wise inventory distribution

---

## 📈 Dashboard Features
- Interactive slicers for:
  - Warehouse
  - Product
  - Supplier
  - Inventory Risk
- Visual KPIs for:
  - Inventory Value
  - Net Stock
  - Stock Movement
- Product-level and warehouse-level performance tracking
- Risk-based inventory visibility for quick decision-making

---

## 🔍 Key Business Insights
- Identified products with negative or low stock requiring immediate attention
- Highlighted high-risk inventory impacting business continuity
- Compared warehouse efficiency and inventory holding value
- Analyzed supplier contribution to overall inventory stock
- Provided clear visibility into stock movement trends

---

## ✅ Final Outcome
- Transformed raw inventory data into actionable insights
- Built a professional Excel dashboard for decision support
- Demonstrated strong skills in:
  - Data cleaning
  - KPI creation
  - Business analysis
  - Dashboard storytelling

This project reflects real-world inventory analysis performed by data analysts
in supply chain and operations teams.

---


