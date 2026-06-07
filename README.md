# Olist E-Commerce Business Intelligence Solution

## 📌 Project Overview
This project delivers an end-to-end Business Intelligence (BI) pipeline to solve a major retail industry challenge: operational data fragmented across isolated transactional tables. 

Focusing on **Olist** (a leading Brazilian e-commerce marketplace), this solution automates an Extract, Transform, Load (ETL) pipeline using **Alteryx Designer** to clean and combine raw data into a consolidated, 8-column analytical flat table. The refined dataset is designed to feed an interactive executive dashboard in **Microsoft Power BI** to help managers instantly identify logistics bottlenecks, shipping cost impacts, and stock imbalances.

---

## 🛠️ Tech Stack & Architecture

### 1. Data Engineering (Alteryx Designer)
Extracts data from 4 relational raw CSV tables:
* `olist_orders_dataset.csv`
* `olist_order_items_dataset.csv`
* `olist_products_dataset.csv`
* `olist_sellers_dataset.csv`

**Data Pipeline Actions:**
* **Deduplication:** Filters out redundant transaction iterations using the **Unique Tool**.
* **Data Cleansing:** Drops entries missing critical data labels using a targeted **Filter Tool** (`!IsNull([product_category_name])`).
* **Feature Engineering:** Computes business performance metrics like delivery lead times using custom expressions in the **Formula Tool**.
* **Aggregation:** Groups localized regional identifiers and runs statistical metrics through the **Summarize Tool**.

### 2. Data Visualization (Microsoft Power BI)
The curated output table feeds an executive dashboard containing:
* **High-Level KPI Cards:** Real-time visibility into overall financial and physical order volume health.
* **Line and Cluster Column Charts:** Time-series trends correlating macro sales milestones with operational delivery timelines.
* **AI-Driven Decomposition Trees:** Multi-layered root cause analysis mapping performance failures across `State -> City -> Category`.
* **Geographical Bubble Maps:** Spatial visualization tracking shipping overhead costs relative to local freight value footprints.

---

## 📊 Output Data Schema
The Alteryx ETL workflow generates a highly optimized table with the following 8 core attributes structured to power interactive dashboards:

| Field Name | Data Type | Purpose in Power BI |
| :--- | :--- | :--- |
| `seller_state` | String / Geo | Region Analysis & Map Plots |
| `seller_city` | String | Local Breakdown in Decomposition Trees |
| `product_category_name` | String | Matrix Table Inventory Sorting |
| `Date_Purchased` | Date | Time-Series Line Charts |
| `Total_Orders` | Integer | Volume Tracker KPI Cards |
| `Product_Sales_Revenue` | Double | Revenue KPI & Trend Columns |
| `Total_Freight_Value` | Double | Map Visual Bubble Sizes |
| `Avg_Delivery_Days` | Double | Performance Overlays (Trend Line) |

---

## 📁 Repository Structure
```text
├── Datasets/                            # Raw transactional source CSV files
|   └── olist_order_items_dataset
|   └── olist_orders_items_dataset
|   └── olist_products_items_dataset
|   └── olist_sellers_items_dataset
├── Alteryx_Workflow/                    # Data pipeline directory
│   └── Olist_ECommerce_BI_Workflow.yxmd # Complete Alteryx XML Workflow file
├── PowerBI_Dashboard/                   # Visualization workspace
│   └──                                  # Power BI Dashboard file
└── README.md                            # Project documentation
