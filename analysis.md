# Analysis Documentation

This document explains each analysis performed on the cleaned dataset and how it was implemented in Excel.

## KPI Analysis
KPIs are calculated on the `KPI` sheet using formulas that reference the cleaned `DATA` sheet (rows 2–1499):

| KPI | Formula Logic | Value |
|---|---|---:|
| Total Sales | Sum of the `Sales` column | 563,332.74 |
| Total Orders | `COUNTA` of `Order_ID` column | 1,498 |
| Total Customers | `COUNTA(UNIQUE(...))` on `Customer_Name` column | 300 |
| Total Products | `COUNTA(UNIQUE(...))` on `Product_Name` column | 200 |
| Total Quantity | `SUM` of `Qty` column | 4,199 |

An additional **Average Sales** value is also calculated on the `KPI` sheet (`AVERAGE` of the `Sales` column) but is not displayed as a card on the dashboard itself.

Not specified: an explicit Average Order Value (AOV) KPI was not built into the dashboard; it could be derived as Total Sales ÷ Total Orders as a future enhancement.

## Top 10 Products
A PivotTable was built on the `CHARTS` sheet summarizing `Sum of Sales` grouped by `Product_Name`, sorted in descending order and filtered to the top 10 results. This PivotTable feeds a PivotChart (horizontal bar chart) shown on the dashboard under "Top 10 Products." Based on this PivotTable, Product_30 has the highest total sales among all products, followed by Product_139 and Product_12.

## Sales Over Days
The cleaned `DATA` sheet includes a derived `Day` column (day of week, extracted from `Order_Date`). A PivotTable on the `CHARTS` sheet aggregates `Sum of Sales` by `Day`, and the days are ordered chronologically (Sunday through Saturday) rather than alphabetically, so the resulting PivotChart (area chart) reads as a proper weekly trend line. Thursday and Sunday show the highest total sales by day, while Monday shows the lowest.

## Sales by Payment Mode
Sales are broken down by the standardized `Payment_Method` field (Card, Cod, Gpay, Netbanking, Phonepe, UPI, Wallet) using a PivotChart (pie chart) on the dashboard, showing the proportion of total sales attributable to each payment method.

## Sales by Category
Sales are compared across the standardized `Category` field (e.g. Snacks, Fruits, Essentials, Beverages, Baby, and others) using a PivotChart (horizontal bar chart) on the dashboard, allowing quick visual comparison of category-level performance.

## Interactive Filtering
Two slicers — **City** and **Payment_Method** — are connected to the PivotTables/PivotCharts that power the dashboard. Selecting a value in either slicer filters all connected charts and KPI values simultaneously, so a user can, for example, view Top 10 Products, Sales Over Days, and category/payment breakdowns for a single city (or a single payment method) without rebuilding any chart manually.

Not specified: exact sales figures for each individual city or payment method are not restated here — these can be viewed directly and interactively by applying the slicers in the workbook.
