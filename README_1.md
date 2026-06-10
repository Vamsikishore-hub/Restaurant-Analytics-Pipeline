# Restaurant Order and Customer Preference Analytics Pipeline

A large-scale data engineering pipeline built on Apache Spark and Delta Lake that processes 100,000 restaurant orders through a Medallion Architecture (Bronze → Silver → Gold) to generate actionable business intelligence.

Built and executed on **Databricks** using PySpark, Delta Lake, and Spark SQL.

---

## Prerequisites

Before you begin, make sure you have access to:
- **Databricks Workspace** — Community Edition is free at [databricks.com](https://www.databricks.com/try-databricks)
- **Python 3.8+** with PySpark (pre-installed on Databricks)

---

## Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Vamsikishore-hub/restaurant-analytics-pipeline.git
   ```

2. **Import the Notebook into Databricks**:
   - Open your Databricks workspace
   - Click **Workspace** → **Import**
   - Upload `Restaurant_Order_and_Customer_Preference_Analytics_Pipeline.ipynb`

3. **Attach a Cluster**:
   - Create or attach a cluster (Databricks Runtime 13.0+ recommended)
   - Single-node cluster is sufficient for this workload

4. **Run All Cells**:
   - Click **Run All** or execute cells sequentially
   - Full pipeline completes in under 2 minutes

---

## How It Works

The pipeline follows a **Medallion Architecture** — a standard industry pattern for lakehouse data engineering:

```
Raw Data (100K records)
        │
        ▼
┌───────────────────┐
│   Bronze Layer    │  Raw ingestion → Delta table (restaurant_bronze)
│   Raw Ingestion   │  No transformations, preserves source fidelity
└────────┬──────────┘
         │
         ▼
┌───────────────────┐
│   Silver Layer    │  Cleaning + Feature Engineering
│   Cleaned Data    │  → total_amount, hour_of_day, day_of_week,
│                   │  → peak_hour flag, customization_label
└────────┬──────────┘
         │
         ▼
┌───────────────────┐
│    Gold Layer     │  Aggregated analytics table (restaurant_orders)
│  Business Ready   │  Optimized for BI queries and reporting
└───────────────────┘
```

---

## Dataset

Simulated dataset of **100,000 restaurant orders** with the following schema:

| Column | Type | Description |
|---|---|---|
| order_id | String | Unique order identifier |
| item_name | String | Menu item (Chicken Bowl, Burger, Pizza Slice, etc.) |
| item_type | String | Category (Main, Snack, Healthy, Drink) |
| quantity | Integer | Number of items ordered |
| price | Double | Unit price |
| order_time | Timestamp | Date and time of order |
| order_mode | String | Online or In-Store |
| city | String | Los Angeles, San Francisco, San Diego |
| customization_flag | Integer | 1 = Customized, 0 = Standard |

---

## Analytical Queries

| Query | Description |
|---|---|
| Revenue by City | Total revenue and order count per city |
| Top Menu Items | Most ordered items by frequency |
| Peak Hour Analysis | Order volume by hour of day |
| Online vs In-Store | Average order value comparison by order mode |
| Customization Analysis | Standard vs customized order patterns |
| Daily Revenue Trend | Time-series revenue across the date range |
| Window Function | Highest revenue item per city using `ROW_NUMBER()` |

---

## Key Insights

- **San Francisco** generated the highest total revenue, followed by Los Angeles and San Diego
- **Chicken Bowl** was the top revenue-generating item across all three cities
- Peak ordering activity was observed between **2 PM and 4 PM** and late evening hours
- **Online orders** had a slightly higher average order value than in-store orders
- Standard and customized orders were nearly equal in volume (~50K each), with similar average values
- Daily revenue remained consistent at ~$195K/day across the 11-day period

---

## Tech Stack

| Layer | Technology |
|---|---|
| Data Processing | Apache Spark (PySpark) |
| Storage Format | Delta Lake |
| Analytics | Spark SQL |
| Platform | Databricks |
| Language | Python 3 |
| Architecture | Medallion (Bronze / Silver / Gold) |

---

## Project Structure

```
restaurant-analytics-pipeline/
├── Restaurant_Order_and_Customer_Preference_Analytics_Pipeline.ipynb
└── README.md
```

---

## Affiliation

Built by **Vamsi Kishore Nallagopu**
Degree: M.S. Computer Science
Institution: California State University, San Bernardino
[GitHub](https://github.com/Vamsikishore-hub) | [LinkedIn](https://www.linkedin.com/in/vamsi-kishore-nallagopu-097707240/)
