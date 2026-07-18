# E-Commerce Sales & Customer Analytics

End-to-end analysis of 100K+ orders from the Olist Brazilian E-Commerce dataset, using Python, SQL, and Power BI to uncover revenue drivers, customer segments, and delivery performance issues — with business recommendations, not just charts.

## Business Problem

Olist is a Brazilian e-commerce platform connecting small sellers to major marketplaces. This project analyzes their order, customer, and delivery data to answer:
- Which product categories and regions drive the most revenue?
- How should customers be segmented, and where's the biggest retention opportunity?
- Does delivery delay actually hurt customer satisfaction, and by how much?

## Tools Used
- **Python (Pandas)** — data cleaning, merging 9 relational tables, feature engineering (RFM, delivery delay), handling missing values and duplicates
- **SQL (SQLite)** — business-question queries (revenue by category, monthly trends, top sellers, regional breakdown, RFM segment summary)
- **Power BI** — interactive dashboard with KPIs, trend lines, segment visuals, and a state-level slicer

## Key Findings

1. **At Risk customers hold the highest total revenue of any segment** — ₹3.96M across 22,230 customers (23% of the base) — larger than the "Champions" segment (₹2.76M). This makes targeted win-back campaigns the single highest-ROI retention opportunity.

2. **Health & Beauty (₹1.46M) and Watches/Gifts (₹1.32M) generate the highest revenue despite fewer orders** than categories like Bed/Bath/Table (9,272 orders) — indicating a higher average order value. These premium categories are worth prioritizing in marketing spend, while high-volume categories need a different, volume-driven strategy.

3. **Review scores drop most sharply once deliveries are 8+ days late**, while 1-3 day delays show only a minor impact. This means logistics investment has the highest payoff when focused on preventing long delays, not minor slippage.

4. **The business is geographically concentrated in São Paulo (SP)** — SP customers alone generate ₹6.07M in revenue (3x the next closest state, Rio de Janeiro at ₹2.17M), and 9 of the top 10 sellers by revenue are also based in SP. This concentration is a risk worth flagging for regional diversification.

5. **Monthly revenue grew consistently from late 2016 through 2018**, peaking in November 2017 (₹1.2M) — likely a seasonal/Black Friday effect. Data coverage ends mid-2018, reflecting the dataset's collection window rather than an actual business decline.

## Dashboard

![Dashboard Screenshot](images/dashboard_screenshot.png)

The dashboard includes:
- KPI cards (total revenue, total orders)
- Monthly revenue trend line
- Top 10 categories by revenue
- Customer segment breakdown (RFM)
- Delivery delay vs. review score comparison
- Interactive state-level slicer

## Project Structure
data/processed/     - Cleaned datasets and exports used for Power BI (raw data excluded due to size)
notebooks/          - Python notebooks for data cleaning, merging, RFM segmentation, feature engineering
sql/queries.sql     - Documented SQL queries for all business questions
dashboard/          - Power BI (.pbix) dashboard file
images/             - Dashboard screenshot

## Methodology

1. **Data Cleaning**: Merged 9 relational tables (orders, customers, products, sellers, payments, reviews, geolocation) using appropriate join types; handled missing values contextually (e.g., undelivered orders naturally lack delivery timestamps) and deduplicated geolocation data by zip prefix.
2. **Feature Engineering**: Calculated delivery delay (actual vs. estimated delivery date), monthly order periods, and item-level revenue.
3. **RFM Segmentation**: Scored all customers on Recency, Frequency, and Monetary value using quintile-based scoring, then classified them into six actionable segments (Champions, Loyal Customers, At Risk, Lost, New Customers, Needs Attention).
4. **SQL Analysis**: Loaded the cleaned dataset into SQLite and wrote queries answering each business question independently of the Python analysis, to demonstrate both toolsets.
5. **Dashboard**: Built an interactive Power BI dashboard translating each finding into a visual, paired with a written business recommendation.

## How to Reproduce

1. Download the raw dataset from [Kaggle - Olist Brazilian E-Commerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
2. Place the extracted CSVs into `data/raw/`
3. Run the notebook(s) in `notebooks/` to clean, merge, and export the data
4. Open `dashboard/ecommerce_dashboard.pbix` in Power BI Desktop to view the interactive dashboard

## Author

**Pratyush Sachan**
[https://www.linkedin.com/in/pratyushsachan/](#) | [GitHub](https://github.com/pratyushsachan/Ecommerce-Sales-Analytics)
