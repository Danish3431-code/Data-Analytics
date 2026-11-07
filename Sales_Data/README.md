# 📊 Sales Performance Dashboard (Excel)

An interactive Excel dashboard built from **1,200 sales orders (Jan – Dec 2024)** to answer the questions a sales manager actually asks: *Which region sells the most? Which category leads? Who are the top reps? When do sales peak? How do customers pay?*

Built with **Excel Tables, Calculated Columns, Pivot Tables, Pivot Charts, Slicers and formulas** – no macros, no external tools.

---

## 🎯 Key Insights

| Metric | Result |
|---|---|
| Total sales (2024) | **≈ 244.4 M** (₹24.4 Cr) |
| Total orders / units sold | 1,200 rows / 9,626 units |
| Average order value | ≈ 203.7 K |
| Average discount | ≈ 7.2 % |
| Top region | **South** – 69.6 M (28.5 %) |
| Weakest region | East – 53.7 M (22.0 %) |
| Top category | **Grocery** – 66.1 M (27.0 %) |
| Top product | Oil – 18.2 M |
| Top sales rep | **Vikas** – 33.9 M (13.9 %), followed by Priya and Arjun |
| Best month | **November** – 26.4 M |
| Weakest month | March – 16.9 M |
| Most-used payment mode | UPI (316 orders), then NetBanking (314) |
| Top city | Chennai – 26.5 M |

**Takeaways**
- South and North together bring in ~56 % of revenue.
- Sales are fairly balanced across categories (23–27 %), with Grocery slightly ahead.
- Q4 is the strongest period (Oct–Nov peak), while March is the clear dip.
- Payment modes are almost evenly split – no single channel dominates.

---

## 🗂️ Workbook Structure

| Sheet | Purpose |
|---|---|
| **Full Reports** | Main dashboard – all charts together with slicers for interactive filtering |
| **Region Wise Sales** | Pivot + bar chart of sales by region |
| **Category wise sales** | Pivot + pie chart of sales by category |
| **Month Trend** | Pivot + line chart of monthly sales trend |
| **Top Sales Rep** | Pivot + bar chart ranking sales reps |
| **Payment Mode** | Pivot + pie chart of order count by payment mode |
| **Sales_Raw_Data** | Source data, stored as an Excel Table named `SalesData` |
| **Analysis Sheet** | Business questions answered with formulas (`SUMIF`, `COUNTIFS`, `AVERAGEIFS`, lookup) |

---

## 🧾 Data Dictionary (`Sales_Raw_Data`)

| Column | Description |
|---|---|
| OrderID | Unique order identifier |
| OrderDate | Date of order (2024-01-01 → 2024-12-31) |
| Region | East / North / South / West |
| City | 12 cities |
| Category | Clothing / Electronics / Furniture / Grocery |
| Product | 16 products (e.g. Mobile, Chair, Jacket, Rice, Oil) |
| SalesRep | 8 sales representatives |
| Quantity | Units ordered |
| UnitPrice | Price per unit |
| Discount% | Discount applied |
| PaymentMode | Card / Cash / NetBanking / UPI |
| TotalSales | Order revenue after discount |
| **Month** *(calculated)* | `=TEXT([@OrderDate],"mmm")` |
| **Sales Level** *(calculated)* | `HIGH` if > 50,000 · `MEDIUM` if > 20,000 · otherwise `LOW` |
| **Net Per Unit** *(calculated)* | `=[@TotalSales]/[@Quantity]` |

---

## 🛠️ Excel Skills Demonstrated

- Excel **Tables** with structured references (`SalesData[TotalSales]`)
- **Calculated columns** using `TEXT`, nested `IF`
- **Pivot Tables** and **Pivot Charts** (bar, pie, line)
- **Slicers** for interactive dashboard filtering
- Analytical formulas: `SUMIF`, `COUNTIFS`, `AVERAGEIFS`, lookups
- Dashboard layout and chart formatting

---

## 🚀 How to Use

1. Download `Sales_Raw_Data.xlsx` and open it in Microsoft Excel (2016 or later recommended for slicers).
2. Go to the **Full Reports** sheet for the complete dashboard.
3. Use the slicers to filter by region, category, etc. – all charts update together.
4. To refresh after adding data: add rows to the `SalesData` table → **Data → Refresh All**.

---

## ⚠️ Data Notes

- Order ID `ORD2186` appears twice with different amounts; it is kept as-is in the dataset and the *Analysis Sheet* looks up both entries.
- Currency is not labelled in the source file; the cities suggest Indian Rupees (₹).

---
