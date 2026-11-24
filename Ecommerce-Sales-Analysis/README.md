E-Commerce Sales Analysis

Note: The dataset is simulated and was created for practice. The results describe this sample data only and do not belong to a real company.

Goal

The goal of this project is to study a year of online store orders and find out which months, product categories, products and regions bring in the most sales. It also measures how much sales fall during the winter months (December, January and February).

Tools
Python
Pandas
Matplotlib
Jupyter Notebook (in VS Code)
Dataset

ecommerce_sales.csv holds 1,015 raw rows and 12 columns: Order_ID, Order_Date, Customer_ID, Category, Product, Region, Quantity, Unit_Price, Discount, Sales, Payment_Method and Rating. The orders cover January to December 2025.

Cleaning Steps

The raw file had a few problems, so I cleaned it before the analysis:

Removed 15 duplicate rows, which left 1,000 orders.
Fixed inconsistent spelling in Category and Region (for example ELECTRONICS became Electronics and north became North).
Filled 8 missing Region values with Unknown.
Filled 13 missing Rating values with the median rating.
Converted Order_Date into a real date and added Month_Num and Month columns.

After cleaning, the data had 1,000 rows, 14 columns and no missing values.

Key Findings
Total sales: 76,509.18 from 1,000 orders.
Best month: November, with 8,285 in sales.
Weakest month: December, with 4,494 in sales.
Best category: Electronics (23,335), followed by Fashion (18,893) and Home & Kitchen (17,213).
Top product: Smartwatch, with 7,605 in sales.
Top region: North, with 18,233 in sales.
Winter effect: average monthly sales in December to February were 31.8% lower than in the other months.
Charts
Monthly Sales

Monthly Sales

Total Sales by Category

Sales by Category

Top 10 Products by Sales

Top Products

Region-wise Sales

Region Sales

How to Run
Install the required libraries:
pip install pandas matplotlib
Keep ecommerce.ipynb and ecommerce_sales.csv in the same folder.
Open ecommerce.ipynb in VS Code or Jupyter.
Click Run All.

The notebook cleans the data, prints the results, saves the four charts in the images folder, and writes ecommerce_sales_cleaned.csv and insights.txt.

Project Structure
E-commerce sales/
├── ecommerce.ipynb
├── ecommerce_sales.csv
├── ecommerce_sales_cleaned.csv
├── insights.txt
├── README.md
└── images/
├── 1_monthly_sales.png
├── 2_sales_by_category.png
├── 3_top_products.png
└── 4_region_sales.png
Author

Danish GitHub: Danish3431-code
