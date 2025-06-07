# 📘 Procurement Performance ETL & Analytics

This project presents an end-to-end ETL and analytics pipeline focused on **procurement performance** for a liquor retail and wholesale business. It aims to improve **vendor selection**, **inventory turnover**, and **cost efficiency** by transforming and analyzing multi-source transactional data.


---

## 🧠 Business Context

Effective inventory and sales management are critical for optimizing profitability in the retail and wholesale liquor industry. Companies must ensure they are not incurring losses due to:
- Inefficient vendor pricing
- High capital Lock-in due to Low inventory turnover
- Dependency on underperforming vendors
  

## 🎯 Project Objectives
The goal of this analysis is to support **data-driven procurement strategy** by building a complete ETL and analytics pipeline. Key business objectives include:


- 📉 **Identify underperforming brands** that require promotional or pricing adjustments  
- 🏆 **Determine top vendors** contributing to overall sales and gross profit  
- 📦 **Analyze the impact of bulk purchasing** on unit costs to identify cost-saving opportunities  
- 🔄 **Assess inventory turnover** to reduce holding costs and improve supply chain efficiency  
- 📊 **Investigate profitability variance** between high-performing and low-performing vendors using statistical measures
  

---

## 🧮 Dataset Overview

The data was provided in CSV format and includes:

- **Sales**: Quantity, price, tax, vendor, brand, store, dates  
- **Purchases**: Quantity, price, vendor info, invoice and PO dates  
- **Vendor Invoice**: Freight costs and payment metadata  
- **Inventory**: Opening and closing stock  
- **Pricing Table**: Purchase and retail price per brand

This raw data was modeled into a relational schema using SQLite.

---


## 🧱 Data Modeling
https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/Untitled.svg

Six core tables were modeled:
- `sales`, `purchases`, `purchase_prices`, `vendor_invoice`, `begin_inventory`, `end_inventory`

Key relationships:
- One-to-many between inventory and sales/purchases
- Many-to-one between vendors and products
- Links between purchase records and invoice metadata

This schema allowed for efficient joins and insights across brands, vendors, and dates.

---


## ⚙️ ETL & Logic Flow

for Ingestion : https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/ingestion_db.ipynb
### 🔄 ETL Pipeline:
1. **Extract**: Loaded CSVs using Python (Pandas)
2. **Transform**:
   - Cleaned, standardized, and joined across tables
   - Created **CTEs** for modular logic
3. **Load**: Final summary tables written back to SQLite

the final aggregated dataset : https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/Transformation%26Load.ipynb
### 📌 Final SQL Output Table:
- `vendor_sales_summary` includes:
  - Purchase price vs actual sale price
  - Sales & purchase quantities
  - Excise tax & freight cost impact
  - Inventory and brand-level insights

---


## 📊 Key Insights
Business queries : https://github.com/shiv-shankar-kumar/Procurement-Performance-ETL-Analytics/blob/main/VP_Analysis.ipynb

| Business Question | Answered Through |
|-------------------|------------------|
| Which brands underperform despite high margins? | Sales & margin filters on final summary |
| Who are the top vendors by sales and profitability? | Grouped by VendorName and Brand |
| Does bulk purchasing reduce unit cost? | Volume vs unit price analysis |
| Which vendors have slow inventory turnover? | On-hand stock vs sales ratio |
| How much capital is locked in unsold inventory? | Inventory × unit cost calculations |
| What's the margin variability across vendors? | 95% CI using Seaborn/Matplotlib |

---


## 💰 Business Impact Summary

- **Total Sales**: $441M  
- **Total Purchases (with Freight)**: $307.34M  
- **Gross Profit**: $134.07M  
- **Overall Gross Margin**: **30.37%**  
- **Unsold Capital Locked**: **$2.71M**  
- > These insights supported vendor pruning, pricing decisions, and capital efficiency improvements.



