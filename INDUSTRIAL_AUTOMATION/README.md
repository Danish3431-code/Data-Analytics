🏭 Industrial Sensor Data Cleaning & Downtime Analysis (Excel)

An Excel project that turns 560 messy machine sensor records into 525 clean, analysis-ready rows and uses Pivot Tables, Pivot Charts and Slicers to find which machines lose the most production time.

Note: The dataset is simulated (synthetic) industrial sensor data created for practice. Findings illustrate the method and are not from a real factory.

🎯 Business Problem

Maintenance and production managers need to know which machines cause the most lost production time, so repair effort goes where it matters. The raw sensor log could not answer this: it contained duplicate rows, blank rows, inconsistent names, text dates and impossible sensor values, so any report built on it would have been wrong.

How this project solves it: the data was cleaned and standardized first, then analysed to show where downtime comes from, how often each machine stops, and how downtime relates to machine status and temperature. This lets a manager prioritize maintenance with confidence.

📈 Key Insights
#	Insight
1	Machine-A has the highest total downtime: 1,510 of 3,925 minutes (38%).
2	Machine-C stops most often: 60.4% of its records include downtime (Machine-A 55.8%, Machine-B 54.6%).
3	Stopped status accounts for the largest share of downtime: 1,260 minutes (about 32%).
4	Machines in Error status run about 4.7 °C hotter than Running machines (66.5 °C vs 61.8 °C).
5	Operator output is similar (137 to 144 units on average), so no operator clearly outperforms the others.
6	Downtime is flat across the two months: Oct 1,945 min vs Nov 1,980 min, showing no major trend.

Recommendation: inspect Machine-A first (largest total loss) and Machine-C next (most frequent stoppages), and investigate why so much downtime is logged under Stopped status.

🧹 Data Cleaning (560 raw rows → 525 clean rows)
Issue found	Count	Action
Blank rows	5	Deleted
Exact duplicate rows	35	Removed
Machine name inconsistencies (spaces, case, separators)	130	Standardized to MACHINE-A/B/C
Operator blank	42	Set to Unknown
Operator spacing / case	55	TRIM + PROPER
Status blank	30	Set to Unknown
Status typos / case	50	Corrected
Plant and Line stored in one cell	525	Split with Text to Columns
Dates stored as text	65	Converted to real dates
Temperature invalid / missing	29	Replaced with median
Vibration invalid / missing	23	Replaced with median
Pressure invalid / missing	23	Replaced with median
Energy invalid / missing	23	Replaced with median
Production output invalid / missing	29	Replaced with median
Downtime invalid / missing	21	Set to 0 (assumption: no downtime recorded)

Valid sensor ranges used: Temperature 20–120 °C, Vibration 0.5–15 mm/s, Pressure 50–200 PSI, Energy 100–400, Production 50–250 units, Downtime 0–60 min. Values outside these ranges were treated as sensor errors.

Added columns: Month and Has_Downtime (1 if downtime > 0, else 0).

🗂️ Workbook Structure
Sheet	Purpose
Dashboard	All 6 charts on one page with slicers
P1_Machine_Downtime	Total downtime by machine
P2_Downtime_Frequency	% of records with downtime by machine
P3_Operator_Output	Average production output by operator
P4_Status_Temperature	Average temperature by machine status
P5_Status_Downtime	Downtime by machine status
P6_Month_Trend	Monthly downtime trend
Clean_Data	Cleaned data stored as an Excel Table (CleanData)
Cleaning_Log	Every cleaning issue, count and action
Raw_Data	Original untouched data
🧾 Data Dictionary
Column	Description
Timestamp	Date and time of the record
Machine	MACHINE-A / MACHINE-B / MACHINE-C
Operator	Ali, Ahmed, Ayesha, Bilal, Sara or Unknown
Plant, Line	Plant-1/2 and Line-A/B/C
Temperature_C	Machine temperature (°C)
Vibration_mm_s	Vibration (mm/s)
Pressure_PSI	Pressure (PSI)
Energy_Consumption	Energy used
Production_Output	Units produced
Status	Running / Maintenance / Stopped / Error / Unknown
Downtime_Minutes	Minutes lost
Month	Month of the record (Oct / Nov)
Has_Downtime	1 if downtime > 0, otherwise 0
🛠️ Skills Demonstrated
Data cleaning: removing duplicates and blank rows, TRIM, UPPER, PROPER, SUBSTITUTE, Text to Columns, text-to-date conversion
Handling missing values and outliers with valid ranges and median imputation
Excel Tables and calculated columns
Pivot Tables, Pivot Charts and Slicers
Dashboard design and business insight writing
Documenting assumptions in a cleaning log
⚠️ Limitations
Simulated dataset, covering about two months (Oct–Nov 2025).
Missing values were filled with the median, and missing downtime was set to 0. These are assumptions and could slightly understate or overstate results.
30 records have status Unknown and 42 have operator Unknown.
🚀 How to Use
Download the .xlsx file and open it in Microsoft Excel.
Open the Dashboard sheet for the full overview.
Use the slicers to filter by machine, operator or status.
See Cleaning_Log for every data fix, and Raw_Data for the original data.
