# Dashboard Guide

This document walks through the `REPORT` sheet (the final dashboard) from top to bottom.

## Layout Overview
The dashboard uses a purple-and-white theme with a header banner, a row of KPI cards, two slicers on the left, and four charts arranged across the remaining space, along with a small Zepto-inspired logo for branding.

## KPI Cards
Five KPI cards sit across the top of the dashboard, each with an icon and a live value pulled from the `KPI` sheet:

- **Total Sales** — 563,332.74
- **Total Orders** — 1,498
- **Total Customers** — 300
- **Total Products** — 200
- **Total Quantity** — 4,199

## Slicers
Two slicers are positioned on the left side of the dashboard:

- **City** — filters by Bangalore, Delhi, Mumbai, or Not Available.
- **Payment_Method** — filters by Card, Cod, Gpay, Netbanking, Phonepe, UPI, or Wallet.

Both slicers are connected to every PivotTable/PivotChart on the dashboard, so any selection updates all visuals and KPI values together.

## Charts

| Dashboard Element | Purpose |
|---|---|
| Total Sales | Overall sales value |
| Total Orders | Number of orders |
| Total Customers | Unique customers |
| Total Products | Products represented |
| Total Quantity | Quantity sold |
| Top 10 Products | Best-performing products |
| Sales Over Days | Day-wise sales trend |
| Sales by Payment Mode | Payment distribution |
| Sales by Category | Category comparison |

- **Top 10 Products** (bar chart) — answers "which products generate the most sales?"
- **Sales Over Days** (area chart) — answers "how does sales volume trend across the days of the week?"
- **Sales by Payment Mode** (pie chart) — answers "which payment methods do customers use most?"
- **Sales by Category** (bar chart) — answers "which product categories perform best?"

## Dashboard Usage
1. Open `zepto_sales_dashboard.xlsx` and go to the `REPORT` sheet.
2. Review the KPI cards at the top for a quick overall summary.
3. Click a value in the **City** slicer to filter all charts and KPIs to that city; click it again (or use the clear-filter icon) to remove the filter.
4. Click a value in the **Payment_Method** slicer to filter by payment method; both slicers can be applied together.
5. Read the **Top 10 Products** chart to see which products are driving the most sales under the current filter.
6. Read the **Sales Over Days** chart to see which days of the week have higher or lower sales.
7. Read the **Sales by Payment Mode** and **Sales by Category** charts to compare performance across payment methods and categories.
8. Clear both slicers to return to the full, unfiltered dataset view.
