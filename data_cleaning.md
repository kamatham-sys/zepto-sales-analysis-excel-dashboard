# Data Cleaning Documentation

This document describes the data-cleaning workflow applied to the raw Zepto sales dataset before it was used for analysis and dashboarding.

## 1. Raw Data Preservation
The original dataset (`zepto_sales_raw_data.xlsx`, sheet `Sheet1`) was never modified. It contains 1,500 order records across 28 columns exactly as originally provided. All cleaning was performed on a separate, dedicated `DATA` sheet inside `zepto_sales_dashboard.xlsx`.

**Why raw data is not modified:**
- It preserves a single source of truth that can always be referenced if a cleaning step needs to be reviewed or redone.
- It allows cleaning logic to be verified against the original values.
- It avoids silently losing information — anything removed or corrected during cleaning can still be traced back to the original record.

## 2. Duplicate Checking
`Order_ID` values in the raw dataset were checked for duplicates. All 1,500 `Order_ID` values were found to be unique — no duplicate order records were present.

## 3. Missing-Value Checking
The `City` column in the raw data contained blank/missing entries for some records. These were not left blank in the cleaned dataset; they were labeled `Not Available` so they could still be tracked, filtered, and displayed on the dashboard (visible as a distinct slicer option).

## 4. Data-Type Validation
`Order_Date` was checked for consistent formatting. The majority of records used a standard date format, but two records (`O0004`, `O0005`) stored the date as text in a different format (e.g. `15 Jan 2025`) rather than the standard format used across the rest of the dataset. Because these two records could not be reliably aligned with the rest of the date-based analysis (Month/Day extraction), they were excluded from the cleaned dataset. This accounts for the difference between 1,500 raw records and 1,498 cleaned records.

## 5. Categorical-Value Validation & Standardization
Several categorical columns contained inconsistent casing and spelling variants in the raw data. These were standardized in the cleaned dataset:

**Category** — raw values included variants such as `frozen` / `Frozen`, `FRUITS ` (with trailing space) / `Fruits`, `DIARY` / `Dairy`, `veg` / `Veg`, `snaks` / `Snacks`, and `bevrage` / `Beverages`. These were consolidated into 10 standardized category labels: Bakery, Baby, Beverages, Dairy, Essentials, Frozen, Fruits, Other, Snacks, Veg.

**Payment_Method** — raw values included variants such as `upi` / `UP I` / `UPI`, `COD`, `GPay`, `PhonePe`, and `NetBanking`. These were standardized into consistent labels: UPI, Cod, Gpay, Phonepe, Netbanking, Card, Wallet.

**City** — standardized to: Bangalore, Delhi, Mumbai, Not Available.

## 6. Invalid-Value Detection
One record in the raw dataset contained an invalid value in the `Delivery_Status` field, where a numeric sales-related value appeared instead of a valid categorical delivery status (expected values: Delivered, Cancelled, Failed, Returned). This was identified during the cleaning process and corrected in the cleaned dataset. The original record in the raw data was left untouched — only the cleaned copy was corrected.

## 7. Numerical-Column Validation
Numeric fields (`Qty`, `Price`, `Discount`, `Subtotal`, `Tax`, `Delivery_Fee`, `Surge_Fee`, and the sales/total value) were checked to confirm they held valid numeric data. The raw `Total` column was carried into the cleaned dataset as `Sales` and used as the basis for all sales-value calculations and KPIs.

## 8. Standardization
In addition to the categorical standardization above, `Month` and `Day` (day of week) columns were derived from `Order_Date` in the cleaned dataset to directly support the "Sales Over Days" analysis without repeated date parsing in every PivotTable.

Several columns present in the raw dataset (e.g. `Pincode`, `Delivery_Slot`, `Warehouse`, `Rider_ID`, `Substituted`, `Refund_Amount`, `Reason`, and an unlabeled column) were not required for the sales KPIs and visuals defined for this dashboard, so they were not carried into the cleaned `DATA` sheet.

## 9. Final Validation
After cleaning, the `DATA` sheet was checked to confirm:
- Row count: 1,498 records (down from 1,500 raw records, per the date-format exclusion described in Section 4).
- 300 unique customers and 200 unique products, matching the dashboard KPI cards.
- All categorical fields (`City`, `Category`, `Payment_Method`, `Delivery_Status`) contain only the standardized, expected values with no remaining case/spelling inconsistencies.

This cleaned dataset was then used as the single data source for all PivotTables, PivotCharts, KPI formulas, and the final dashboard.
