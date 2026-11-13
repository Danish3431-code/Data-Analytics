# Industrial Sensor Dashboard: Machine Downtime Analysis

A two-page Power BI dashboard that looks at sensor and production data from industrial machines. It shows where downtime happens, which machines and statuses cause it, and how temperature and vibration readings relate to risk.

## Dashboard Preview

**Page 1: Industrial Dashboard**

<img width="605" height="343" alt="powerbi_1" src="https://github.com/user-attachments/assets/3fb437c3-a0ba-4ca9-ae9d-6096f831948c" />

<img width="606" height="341" alt="powerbi_2" src="https://github.com/user-attachments/assets/fdf0b0ca-4777-4695-9d63-07603caf8139" />



## Project Goal

Machines that stop unexpectedly cost time and production. This project turns raw sensor readings into one clear view so a person can quickly answer questions like:

- Which machine loses the most time to downtime?
- Which machine status is linked with the longest stops?
- Do higher temperature and vibration readings go together with longer downtime?
- How do temperature and vibration change over time?

## Dataset

The report uses one cleaned table called `CleanData` with 14 fields:

| Field | Meaning |
|---|---|
| Timestamp | Date and time of the reading |
| Plant, Line, Machine | Where the reading came from |
| Operator | Person running the machine |
| Status | Machine state (Running, Stopped, Maintenance, Error, Unknown) |
| Month | Month of the reading |
| Downtime_Minutes | Minutes the machine was down |
| Has_Downtime | 1 if there was downtime, otherwise 0 |
| Production_Output | Units produced |
| Temperature_C | Temperature in degrees Celsius |
| Vibration_mm_s | Vibration in mm/s |
| Pressure_PSI | Pressure in PSI |
| Energy_Consumption | Energy used |

## DAX Measures

```
Total Downtime   = SUM(CleanData[Downtime_Minutes])
Avg Downtime     = AVERAGE(CleanData[Downtime_Minutes])
Downtime Rate %  = AVERAGE(CleanData[Has_Downtime])
Avg Output       = AVERAGE(CleanData[Production_Output])
Avg Temperature  = AVERAGE(CleanData[Temperature_C])
Avg Vibration    = AVERAGE(CleanData[Vibration_mm_s])
High Risk Records = CALCULATE(COUNTROWS(CleanData), CleanData[Risk Level] = "High Risk")
```

## Risk Level (Calculated Column)

Every record is placed in one of three risk groups using vibration and temperature:

```
Risk Level =
IF(AND(CleanData[Vibration_mm_s] > 6, CleanData[Temperature_C] > 70), "High Risk",
IF(OR(CleanData[Vibration_mm_s] > 5.5, CleanData[Temperature_C] > 68), "Medium Risk", "Low Risk"))
```

- **High Risk:** vibration above 6 and temperature above 70
- **Medium Risk:** vibration above 5.5 or temperature above 68
- **Low Risk:** everything else

## What the Dashboard Contains

**Page 1: Industrial Dashboard**

- 5 KPI cards: Total Downtime, Downtime Rate %, Avg Output, Avg Temperature, High Risk Records
- Total Downtime by Machine
- Downtime Rate by Machine
- Downtime by Machine Status
- Average Downtime by Risk Level (min)
- Records by Risk Level (donut chart)
- Average Production Output by Machine
- Slicers for Machine, Operator and Status

**Page 2: Trends**

- Average Temperature over Time (°C)
- Average Vibration over Time (mm/s)

## Key Findings

- Total downtime is **3,925 minutes**, and downtime appears in **56.8%** of records.
- **Machine A** has the highest total downtime (1,510 min), while **Machine C** has the highest downtime rate (60.4%).
- Records with the **Stopped** status add the most downtime (1,260 min).
- Average downtime rises with risk: **7.0 min** (Low), **8.0 min** (Medium) and **10.4 min** (High). Higher sensor readings go together with longer stops.
- **37** records fall in the High Risk group.

## How to Open the Project

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
2. Download or clone this repository.
3. Open `Industrial_Sensor_Dashboard.pbix`.
4. Use the slicers on Page 1 to filter by Machine, Operator or Status.

## Repository Structure

```
├── Industrial_Sensor_Dashboard.pbix
├── images/
│   ├── powerbi_dashboard.png
│   └── powerbi_trends.png
└── README.md
```

## Skills Practised

- Data modelling and DAX measures in Power BI
- Creating a calculated column for risk grouping
- Building KPI cards, charts, slicers and a multi-page report
- Turning sensor data into insights about machine downtime

## Author

**Danish**
GitHub: [Danish3431-code](https://github.com/Danish3431-code)
