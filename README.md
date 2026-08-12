# Zepto Sales Analysis & Interactive Excel Dashboard

## Overview
This project analyzes a quick-commerce style sales dataset (1,500 order records) and presents the results through an interactive Excel dashboard. The workbook takes raw, inconsistently formatted order data through a structured cleaning process, calculates key business KPIs, and visualizes performance using PivotTables, PivotCharts, and slicers. The goal of the project is to demonstrate practical, end-to-end Excel data analysis skills — from raw data handling to a recruiter-ready interactive dashboard.

## Project Preview

![Zepto Sales Dashboard](screenshots/dashboard.png)

## Project Objectives
- Clean and prepare raw sales data for analysis
- Identify and standardize inconsistent categorical values (city, category, payment method)
- Calculate core business KPIs (sales, orders, customers, products, quantity)
- Analyze product-level, time-based, and payment-method sales trends
- Build an interactive Excel dashboard using PivotTables, PivotCharts, and slicers
- Present findings in a clear, recruiter- and professor-friendly format

## Dataset
The project uses two separate Excel files:

| File | Purpose |
|---|---|
| `zepto_sales_raw_data.xlsx` | Original, unmodified source data (1,500 records, 28 columns) |
| `zepto_sales_dashboard.xlsx` | Cleaned data, PivotTables, KPI calculations, and final dashboard |

**Dataset source:** Not specified. This is a working analysis dataset used for practicing Excel data cleaning, PivotTable analysis, and dashboard building — it is not claimed to be official Zepto company data.

**Raw vs. Cleaned data:**
- The raw dataset (`zepto_sales_raw_data.xlsx`, sheet `Sheet1`) is kept fully intact and is never edited. It contains the original values exactly as received, including inconsistent text casing, spelling variants, and missing entries.
- The cleaned dataset (`DATA` sheet in `zepto_sales_dashboard.xlsx`) is a separate, standardized version of the same records used for all analysis and dashboarding. It contains 1,498 records after cleaning.

## Data Cleaning
A brief summary is provided here; full details are in [`documentation/data_cleaning.md`](documentation/data_cleaning.md).

- City, Category, and Payment_Method values were standardized (case and spelling inconsistencies such as `upi` / `UP I` / `UPI`, or `snaks` / `Snacks`, were unified into single consistent labels).
- Missing City values were labeled `Not Available` rather than left blank.
- Two records were excluded from the cleaned dataset because their `Order_Date` values were stored in a non-standard text format (e.g. `15 Jan 2025`) inconsistent with the rest of the dataset, and could not be reliably parsed alongside the other date fields.
- One record in the raw data contained an invalid value in the `Delivery_Status` field (a numeric sales-type value instead of a categorical delivery status). This issue was identified during cleaning and corrected in the cleaned dataset — the original raw record was not deleted or altered in the raw file.
- Redundant/unlabeled columns present in the raw data were not carried into the cleaned dataset.
- `Month` and `Day` (day of week) columns were derived from `Order_Date` to support the "Sales Over Days" analysis.

## Analysis Performed
- **Top 10 Products** — Products ranked by total sales value using a PivotTable/PivotChart on the cleaned data.
- **Sales Over Days** — Total sales aggregated by day of the week to observe weekly sales patterns.
- **Sales by Payment Mode** — Total sales broken down across payment methods (Card, Cod, Gpay, Netbanking, Phonepe, UPI, Wallet).
- **Sales by Category** — Total sales compared across product categories (Snacks, Fruits, Essentials, Beverages, Baby, etc.).
- **City-level filtering** — Interactive slicer to filter all charts and KPIs by City.
- **Payment-method filtering** — Interactive slicer to filter all charts and KPIs by Payment Method.

Full breakdown in [`documentation/analysis.md`](documentation/analysis.md).

## KPIs

| KPI | Value |
|---|---:|
| Total Sales | 563,332.74 |
| Total Orders | 1,498 |
| Total Customers | 300 |
| Total Products | 200 |
| Total Quantity | 4,199 |

## Dashboard Features
- **KPI cards** with icons displaying Total Sales, Total Orders, Total Customers, Total Products, and Total Quantity at a glance.
- **Slicers** for City and Payment Method that interactively filter all PivotCharts and KPI values simultaneously.
- **Multiple PivotCharts**: Top 10 Products (bar), Sales Over Days (area), Sales by Payment Mode (pie), Sales by Category (bar).
- **Purple and white theme** with Zepto-inspired branding for a clean, professional look.

Full walkthrough in [`documentation/dashboard_guide.md`](documentation/dashboard_guide.md).

## Tech Stack

| Tool | Purpose |
|---|---|
| Microsoft Excel | Core platform for the entire project |
| PivotTables | Aggregating and summarizing cleaned data |
| PivotCharts | Visualizing PivotTable output |
| Slicers | Interactive City and Payment Method filtering |
| Excel Formulas | KPI calculations (COUNTA, UNIQUE, SUM, AVERAGE) |
| Manual Data Cleaning | Standardizing categorical values and fixing invalid entries |

## Key Features
- Clear separation between raw and cleaned data
- Documented, traceable data-cleaning process
- KPI values calculated with live Excel formulas referencing the cleaned dataset
- Fully interactive dashboard — no macros or external tools required
- Consistent purple/white visual theme with a Zepto-inspired logo

## Project Structure
```
zepto-sales-analysis/
│
├── README.md
├── zepto_sales_raw_data.xlsx
├── zepto_sales_dashboard.xlsx
│
├── documentation/
│   ├── data_cleaning.md
│   ├── analysis.md
│   └── dashboard_guide.md
│
└── screenshots/
    └── dashboard.png
```

## Key Takeaways
- Thursday and Sunday show the highest total sales among the days of the week; Monday shows the lowest, based on the "Sales Over Days" PivotTable.
- The top-performing product in the dataset by total sales is Product_30, followed closely by Product_139 and Product_12.
- January and February account for the large majority of total sales compared to March, based on the underlying monthly PivotTable.
- All other product-, category-, and payment-level comparisons can be explored interactively in the dashboard using the slicers; specific rankings beyond the above are best viewed directly in the workbook rather than restated here.

## How to Use
1. Download `zepto_sales_dashboard.xlsx` from this repository.
2. Open the file in Microsoft Excel (Excel 2016 or later recommended for full slicer/PivotTable support).
3. Go to the `REPORT` sheet to view the dashboard.
4. Use the **City** and **Payment_Method** slicers on the left to filter the KPIs and charts interactively.
5. Refer to the `DATA`, `CHARTS`, and `KPI` sheets to inspect the cleaned dataset, PivotTables, and KPI formulas respectively.

## Future Improvements
- Monthly/yearly sales trend analysis
- Delivery performance analysis (using Delivery_Status and Delivery_Time fields)
- More advanced Excel automation (dynamic arrays, macros)
- Additional KPIs such as Average Order Value and repeat-customer rate
- Power BI version of the dashboard for extended interactivity

## Author
Your Name
B.Tech – Electronics and Communication Engineering
