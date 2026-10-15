# Retail Sales Data Analysis and Interactive Dashboard — Task 1

## Overview
A beginner-to-intermediate Data Science & Data Analytics project demonstrating Python fundamentals applied to a retail sales workflow: load data, validate and clean it, calculate revenue, perform EDA, visualize product/region/monthly performance, and document business insights.

> **Dataset note:** `datasets/raw/retail_sales_raw.csv` is a synthetic practice dataset created for this project. It includes deliberately introduced missing values and duplicate records to demonstrate data cleaning. Do not treat the results as actual company performance.

## Project structure
```text
retail_sales_data_analysis_task1/
├── datasets/
│   ├── raw/retail_sales_raw.csv
│   └── cleaned/retail_sales_clean.csv
├── notebooks/retail_sales_analysis.ipynb
├── scripts/analyze_retail_sales.py
├── reports/
│   ├── eda_report.md
│   ├── summary_metrics.json
│   └── figures/
├── documentation/TASK1_FULL_EXPLANATION.pdf
├── requirements.txt
└── README.md
```

## Setup
Python 3.10+ is recommended (the supplied internship guide lists Python 3.13).
```bash
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\Activate.ps1
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
python scripts/analyze_retail_sales.py
```

## Run in Jupyter
```bash
jupyter notebook
```
Open `notebooks/retail_sales_analysis.ipynb` and run cells from top to bottom.

## Data dictionary
- `Order_ID`: order identifier
- `Order_Date`: order date
- `Customer_ID`: anonymized customer identifier
- `Region`: sales region
- `Product`: product name
- `Category`: product category
- `Quantity`: number of units
- `Unit_Price`: price per unit
- `Discount`: discount fraction (e.g., 0.10 = 10%)
- `Payment_Method`: payment method
- `Gross_Sales`: Quantity × Unit_Price
- `Revenue`: Gross_Sales × (1 − Discount)
- `Month`: calendar month derived from Order_Date

## Cleaning decisions
1. Normalize column-name whitespace.
2. Parse dates and numeric columns explicitly.
3. Remove exact duplicate records.
4. Exclude rows with missing/non-positive quantity because revenue cannot be reliably computed.
5. Label missing region/customer/product/category as `Unknown` rather than inventing values.
6. Replace missing discount with zero and clip discount into [0, 1].
7. Exclude missing or negative unit prices.
8. Create gross sales, net revenue, and month features.

These choices are explicit assumptions; real projects should validate them with a business owner and document alternative approaches.

## Analysis questions answered
- Which products generate the highest revenue?
- Which region performs best?
- What are monthly sales trends?
- What are the key data-quality issues?
- How do quantity, unit price, discount, gross sales and revenue relate?

## Deliverables
- Python source code
- Raw and cleaned CSV datasets
- Jupyter notebook
- EDA report and KPI JSON
- Four visualizations
- Full explanation PDF (included in ZIP and separately supplied)
