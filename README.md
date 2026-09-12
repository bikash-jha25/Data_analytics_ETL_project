# Retail Orders Data Analytics & ETL Project

This repository contains an end-to-end Data Analytics and ETL pipeline project based on the Kaggle Retail Orders dataset. It includes data extraction via Kaggle API, data cleaning/transformation in Python using Pandas, loading into SQL Server using SQLAlchemy, and key business analytics queries written in SQL.

---

## 📁 Project Structure

```text
├── orders data analysis.py    # Python script for Kaggle data extraction, cleaning & SQL Server ingestion
├── sql_code.sql               # SQL queries for data analytics and key business insights
└── README.md                  # Project documentation
```

---

## 🛠️ Tech Stack & Prerequisites

- **Python 3.x**
- **Libraries**: `pandas`, `sqlalchemy`, `kaggle`, `zipfile`
- **Database**: Microsoft SQL Server
- **Dataset**: [Kaggle - Retail Orders Dataset (`ankitbansal06/retail-orders`)](https://www.kaggle.com/datasets/ankitbansal06/retail-orders)

---

## 🚀 Workflow Overview

### 1. Data Ingestion & Cleaning (`orders data analysis.py`)
- Downloads the dataset directly from Kaggle using the Kaggle API.
- Extracts the ZIP archive containing `orders.csv`.
- Cleans data, replacing placeholders (`Not Available`, `unknown`) with `NaN`.
- Calculates calculated fields (`profit`, `sale_price`, etc.) and formats `order_date` to standard datetime.
- Drops obsolete/raw price columns and loads the cleaned data into SQL Server via `SQLAlchemy`.

### 2. SQL Analytics & Insights (`sql_code.sql`)
The SQL script runs business intelligence analytical queries on the ingested database table (`df_orders`):
1. **Top 10 Revenue Generating Products**: Products generating the highest total sales volume.
2. **Top 5 Selling Products by Region**: Window functions (`ROW_NUMBER()`) partitioning products per region.
3. **Month-over-Month Growth Comparison (2022 vs 2023)**: Cross-pivot sales analysis using CTEs and aggregation.
4. **Highest Sales Month per Category**: Identifies peak sales periods across categories.
5. **Highest Growth Sub-Category in 2023**: Calculates year-over-year profit margin improvements per product sub-category.

---

## ⚙️ How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/bikash-jha25/Data_analytics_ETL_project.git
   cd Data_analytics_ETL_project
   ```

2. Setup Kaggle API credential file `kaggle.json` in `~/.kaggle/` directory.

3. Run the Python ETL script to download and load data into your SQL Server database:
   ```bash
   python "orders data analysis.py"
   ```

4. Open your SQL Server client (SSMS / Azure Data Studio) and run the analytical queries in `sql_code.sql`.
