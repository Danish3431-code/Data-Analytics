# 🏭 Industrial Automation – Machine Performance Analysis (Excel)

An Excel dashboard that analyzes **47 machine log records (Oct – Nov 2025)** from three machines to find where downtime comes from, how operators and machines perform, and how machine status relates to temperature.

Built with **Excel data cleaning, Pivot Tables, Pivot Charts and Slicers**.

---

## 🎯 Objectives

- Find which machine loses the most production time
- Compare operator performance by average output
- Understand how machine status relates to temperature
- Spot data-quality problems before drawing conclusions

---

## 📈 Dashboard Charts

| Chart | Question answered |
|---|---|
| Machine-wise Total Downtime (Minutes) | Which machine stops the most? |
| Operator-wise Average Production | Which operator produces the most per record? |
| Status-wise Average Temperature | Do machines run hotter when in error? |

---

## 🔍 Key Insights

### 1. Downtime by machine
| Machine | Total downtime | Records | Records with downtime |
|---|---|---|---|
| MACHINE-A | **85 min** (46 % of total) | 20 | 35 % |
| MACHINE-C | 55 min | 13 | **46 %** |
| MACHINE-B | 45 min | 14 | 29 % |

- Total downtime across all machines: **185 minutes**.
- **Machine-A** loses the most time overall, and it also has the most records (20), so part of this is volume.
- **Machine-C** stops most *often*: almost half of its records include downtime.
- **Machine-B** is the most reliable.

### 2. Operator performance (average production output)
| Operator | Avg output | Records |
|---|---|---|
| Ayesha | **151.6** | 7 |
| Ali | 142.0 | 18 |
| Bilal | 141.5 | 8 |
| Ahmed | 127.1 | 9 |
| Unknown | 125.2 | 5 |

- Ayesha has the highest average output, about **19 % above Ahmed**.
- Ali has the most downtime (70 min), but also the most records (18), so total downtime alone should not be used to judge operators.

### 3. Status vs. temperature
| Status | Avg temperature (°C) | Records |
|---|---|---|
| Error | **72.2** | 3 |
| Stopped | 67.1 | 4 |
| Running | 64.4 | 14 |
| Unknown | 63.9 | 22 |
| Maintenance | 58.9 | 4 |

- Machines in **Error** state run the hottest, about **8 °C above Running**.
- Maintenance records show the lowest temperature.
- The Error average is based on only 3 records, so treat it as an observation, not a rule.

### 4. Extra findings from the raw data
- **Downtime hurts output:** records with downtime average **130.7 units**, records without average **143.2** (about 9 % lower). Correlation between downtime and output is −0.30.
- **Machine-A is the least efficient:** it uses the most energy (266 vs ~250) and produces the least output (134 vs ~142). Output per unit of energy: A = 0.50, B = 0.57, C = 0.57.
- **Maintenance is concentrated on Machine-A:** all 4 maintenance records belong to it.
- **Most downtime happens while "Running":** 110 of 185 minutes, suggesting short micro-stoppages rather than full shutdowns.

---

## 🧹 Data Cleaning

| Issue found | Action |
|---|---|
| 2 records with `Temperature_C = 0` (sensor error / placeholder) | Replaced with blank so they do not distort averages |
| Inconsistent machine names | Standardized into `Machine_Clean` |
| Missing operator names | Labelled `Unknown` |
| Missing / unclear status | Labelled `Unknown` |
| `Pressure_PSI = 121.04` repeated 6 times | Likely filled with the median for missing values; kept as is |

---

## 🗂️ Workbook Structure

| Sheet | Purpose |
|---|---|
| **Report** | Final dashboard with all 3 charts |
| **Machine_Clean&Downtime_Minutes** | Pivot + chart: total downtime by machine |
| **Operator&Production_Output** | Pivot + chart: average output by operator |
| **Status&Temperature_C** | Pivot + chart: average temperature by status |
| **Raw Data of Machine** | Cleaned source data (47 rows) |

## 🧾 Data Dictionary

| Column | Description |
|---|---|
| Timestamp | Date and time of the record |
| Machine_Clean | MACHINE-A / MACHINE-B / MACHINE-C |
| Operator | Ali, Ahmed, Ayesha, Bilal or Unknown |
| Temperature_C | Machine temperature (°C) |
| Vibration_mm_s | Vibration (mm/s) |
| Pressure_PSI | Pressure (PSI) |
| Energy_Consumption | Energy used |
| Production_Output | Units produced |
| Status | Running / Maintenance / Stopped / Error / Unknown |
| Downtime_Minutes | Minutes lost (0, 5, 10 or 15) |
| Month | Month of the record |

---

## ⚠️ Limitations

- Small dataset: **47 records**, and 46 of them are from October.
- **47 % of records have status "Unknown"** (22 of 47), so status-based findings cover only part of the data.
- Findings are **indicative, not statistical proof**.

## 🛠️ Skills Demonstrated

Data cleaning · Handling missing values and outliers · Pivot Tables · Pivot Charts · Slicers · Dashboard design · Business insight writing

## 🚀 How to Use

1. Download the `.xlsx` file and open it in Microsoft Excel.
2. Open the **Report** sheet for the full dashboard.
3. Use the slicer to filter, and **Data → Refresh All** after adding new rows.

