Superstore Sales Analysis — AnalystLab Africa Data Analytics Internship

## Project overview
Advanced business analysis, KPI development, and an interactive Power BI dashboard built on the Superstore Sales Dataset, continued from Week 2 through Week 3.

## Dataset
- **Source file:** `Superstore_Cleaned.csv`
- **Size:** 9,994 order line items, 26 fields
- **Coverage:** United States orders, 2014–2017
- Pre-cleaned fields include Order Year, Order Month, Shipping Delay (Days), and per-line Profit Margin.

## Week 2 recap
Initial exploration and dashboard covering sales, profit, product, customer, and regional performance. Delivered a 3-page Power BI report: Sales Dashboard, Business Insights/Risks/Opportunities, and Business Recommendations.

## Week 3 additions
- **DateTable**: a calculated date dimension (`CALENDAR()`) added and marked as the official Date table, related to `Superstore_Cleaned[Order Date]`, to support time-intelligence measures.
- **8 DAX measures** added to `Superstore_Cleaned`: Total Sales, Total Profit, Profit Margin, Total Orders, Avg Sales per Order, Sales YoY %, Profit YoY %, Loss-Making Line Items.
- **New KPI cards** on the Sales Dashboard page for the three new measures (Avg Sales per Order, Sales YoY %, Loss-Making Line Items), extending the original 5-card KPI row to 8.
- **New slicers**: Category and Sub-Category, added to the Sales Dashboard page alongside the existing Region/Year/Segment slicers.
- **State profitability table** added to the Insights page, sorted by Sum of Profit ascending, surfacing a loss-making state cluster (Texas, Ohio, Pennsylvania, Illinois) beyond what Week 2 showed.
- **YoY growth cards** added to the Insights page alongside the existing monthly trend chart.
- **Key Insight / Risk / Opportunity** callouts added as separate textboxes.

## Key findings (Week 3)
- Profit growth is decoupling from sales growth: 2017 sales grew 20.4% but profit grew only 14.2%.
- Tables (–8.6% margin) and Bookcases (–3.0% margin) are the largest loss-making sub-categories despite steady demand.
- The Central region's weak 7.9% margin is driven by a cluster of loss-making states — Texas, Ohio, Pennsylvania, and Illinois — not Texas alone.
- Discount and Profit show a moderate negative correlation (r ≈ −0.22), concentrated in specific high-loss products.
- Technology, especially Copiers (37% margin), is the strongest area for further investment.

## Deliverables in this repository
1. Power BI dashboard (`.pbix`)
2. Dashboard PDF / screenshots
3. Advanced Data Analysis document
4. Business Insights and Recommendations Report
5. DAX Measures documentation
6. This README

## Tools used
Power BI Desktop, DAX, Excel/CSV data cleaning.

---
*AnalystLab Africa Data Analytics Internship Programme — Week 3 Submission*
