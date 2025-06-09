# 📘 Procurement Performance ETL & Analytics  
An end-to-end data pipeline and analytics solution for procurement optimization in the liquor retail and wholesale industry.

---

## 📌 Project Overview

### 🧠 Background  
In the retail and wholesale liquor business, profitability depends heavily on efficient vendor management, inventory turnover, and cost control. Businesses often suffer losses due to:

- Inefficient vendor pricing  
- High capital lock-in from unsold inventory  
- Dependence on underperforming vendors  

This project leverages ETL (Extract, Transform, Load) techniques to clean and model procurement data, enabling data-driven decisions and operational insights.



### 🎯 Purpose  
This project was built to support strategic procurement decisions by creating a robust ETL pipeline and analytical framework. It focuses on:

- Identifying underperforming brands needing pricing or promotional changes  
- Recognizing top-performing vendors based on sales and gross profit  
- Evaluating cost-saving opportunities through bulk purchases  
- Assessing inventory turnover to minimize holding costs  
- Analyzing profitability variance between vendors using statistical methods  

---

## 🔍 Overview of the Code

The analysis follows a modular structure across multiple Jupyter Notebooks, culminating in a fully functional ETL and reporting process.

---

### 🧱 Data Modeling  
The raw data was provided in CSV format and modeled into a relational schema using SQLite. The schema consists of six core tables:

- `sales`  
- `purchases`  
- `purchase_prices`  
- `vendor_invoice`  
- `begin_inventory`  
- `end_inventory`  

**Key Relationships:**  
- One-to-many between inventory and sales/purchases  
- Many-to-one between vendors and products  
- Links between purchase records and invoice metadata  

**Schema Diagram:**  
📎 [View Schema](https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/Untitled.svg)

---

### ⚙️ ETL Pipeline

#### **Ingestion:**  
🔗 [ingestion_db.ipynb](https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/ingestion_db.ipynb)  
- CSVs loaded using Python and Pandas

#### **Transformation:**  
🔗 [Transformation & Load Notebook](https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/Transformation%26Load.ipynb)  
- Cleaned and standardized datasets  
- Created Common Table Expressions (CTEs) for modular SQL logic  

#### **Load:**  
- Transformed summary tables written back to SQLite

---

### 📌 Final Output Table: `vendor_sales_summary`  
Includes:

- Purchase vs Sale Price  
- Quantity sold/purchased  
- Freight & Excise tax impact  
- Inventory dynamics and brand-level performance  

---

## 📊 Business Insights  
🔗 [Business Queries Notebook](https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/VP_Analysis.ipynb)

| Business Question | Insight Method |
|-------------------|----------------|
| Which brands underperform despite high margins? | Filters on sales and margin in summary table |
| Who are the top vendors by sales and profit? | Grouped by `VendorName` and `Brand` |
| Does bulk purchasing reduce unit cost? | Volume vs Unit Cost analysis |
| Which vendors have slow inventory turnover? | Sales vs On-hand stock ratio |
| How much capital is locked in inventory? | Unit cost × Unsold stock |
| What's the margin variability between vendors? | 95% CI plots using Seaborn and Matplotlib |

---

## 💰 Business Impact Summary  

- **Total Sales:** $441M  
- **Total Purchases (incl. Freight):** $307.34M  
- **Gross Profit:** $134.07M  
- **Overall Gross Margin:** 30.37%  
- **Unsold Capital Locked:** $2.71M  

---

## 🧮 Resources

### **Data Sources**
- Sales, purchases, inventory, and invoice data in CSV format

### **Environment**
- Python 3.x  
- SQLite  

### **Dependencies**
- pandas  
- numpy  
- matplotlib / seaborn  
- sqlite3  
- Jupyter Notebook  

### **Software**
- Jupyter Notebook  
- SQLite Browser  
