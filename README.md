# amitdubli_2511380_part1_data_cleaning
Part 1: Business Data Cleaning, Validation &amp; Excel Reporting

# Sales Orders Data Cleaning and Quality Assessment

## Problem Summary

This project focuses on cleaning, validating, and analyzing a raw sales orders dataset using Python and Pandas. The dataset contained inconsistent text formatting, mixed date formats, missing values, duplicate records, invalid discounts, and business rule violations.

The objective was to transform the raw dataset into a clean, analysis-ready dataset while generating data quality reports, pivot summaries, and comprehensive documentation.

---

## Dataset Description

**Source File:** raw_orders.xlsx

**Records:** 932

**Columns:** 20

| Column         |
| -------------- |
| order_id       |
| order_date     |
| ship_date      |
| customer_id    |
| customer_name  |
| segment        |
| region         |
| state          |
| city           |
| category       |
| sub_category   |
| product_name   |
| ship_mode      |
| quantity       |
| unit_price     |
| discount       |
| sales          |
| cost           |
| profit         |
| payment_status |
| order_status   |

---

## Tools Used

* Python 
* Pandas
* NumPy
* OpenPyXL
* Microsoft Excel (Validation)

---

## Cleaning Steps Performed

### Text Cleaning

* Removed leading and trailing spaces
* Removed multiple spaces
* Standardized capitalization
* Removed unwanted special characters
* Standardized categorical values

### Missing Value Handling

* Filled missing Region values with **Unknown**
* Filled missing Ship Mode values with **Unknown**
* Filled missing Discount values with **0** when valid

### Date Validation

* Converted mixed date formats into a consistent format
* Flagged invalid dates
* Flagged missing dates
* Identified ship dates earlier than order dates
* Calculated shipping delay

### Duplicate Handling

* Removed exact duplicate rows
* Flagged duplicate Order IDs containing conflicting information

### Business Rule Validation

* Validated discount values
* Flagged negative discounts
* Flagged discounts outside the allowed range
* Excluded cancelled and failed transactions from completed sales summaries
* Summarized refunded transactions separately

### Calculated Columns

Created:

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

## Business Rules Applied

| Rule                         | Action                                     |
| ---------------------------- | ------------------------------------------ |
| Missing Region               | Filled with Unknown                        |
| Missing Ship Mode            | Filled with Unknown                        |
| Missing Discount             | Set to 0 only when sales fields were valid |
| Negative Discount            | Flagged                                    |
| Discount above allowed range | Flagged                                    |
| Ship Date before Order Date  | Flagged                                    |
| Cancelled Orders             | Excluded from completed sales              |
| Failed Payments              | Excluded from completed sales              |
| Refunded Orders              | Summarized separately                      |

---

## Data Quality Issues Found

Examples of issues identified:

* Missing values
* Mixed date formats
* Invalid dates
* Negative discounts
* Discounts above valid range
* Exact duplicate rows
* Duplicate order IDs with conflicting values
* Missing Region
* Missing Ship Mode
* Ship dates before order dates

---

## Reports Generated

### Data Quality Report

Includes:

* Missing Value Summary
* Duplicate Summary
* Invalid Discount Summary
* Date Validation Summary
* Order Status Summary
* Sales and Profit Validation
* Final Clean vs Flagged Records

### Pivot Summary Report

Includes:

* Sales and Profit by Region
* Sales and Profit by Category
* Sales by Sub-category
* Order Count by Ship Mode
* Profit Margin by Customer Segment
* Refunded / Cancelled / Failed Orders by Region
* Monthly Sales Trend

---

## Key Business Insights

Examples of insights generated from the cleaned dataset include:

* Highest revenue-generating regions
* Most profitable product categories
* Customer segments with the highest average profit margin
* Most frequently used shipping methods
* Monthly sales trends
* Regions with higher cancelled or refunded order rates
* Data quality issues affecting business reporting

---

## Assumptions

* Discounts are stored as decimal values (0–1).
* Missing Region and Ship Mode values are replaced with **Unknown**.
* Shipping delay is calculated as:
  Ship Date − Order Date
* Profit is calculated as:
  Calculated Sales − Cost
* Profit Margin is calculated as:
  Calculated Profit ÷ Calculated Sales

---

## Limitations

* Ambiguous date formats may require manual verification.
* Category standardization depends on predefined mappings.
* Business validation is limited to the supplied rules.
* Flagged records require manual review before production use.

---

## Screenshots Included

The repository contains screenshots of:

* Raw Dataset
* Cleaned Dataset
* Data Quality Report
* Pivot Summary Report
* Final Output Files

---

## Repository Structure

```
part1_data_cleaning/
├── data/
│   ├── raw_orders.xlsx
│   └── cleaned_orders.xlsx
├── outputs/
│   ├── data_quality_report.xlsx
│   ├── pivot_summary.xlsx
│   └── cleaning_log.md
├── screenshots/
│   ├── raw_data_preview.png
│   ├── cleaned_data_preview.png
│   ├── pivot_summary_1.png
│   └── pivot_summary_2.png
└── README.md
```

---

## Conclusion

The raw sales dataset was successfully cleaned, validated, and transformed into an analysis-ready dataset. Comprehensive quality checks, business rule validations, calculated metrics, pivot reports, and documentation were generated to support reliable business reporting and decision-making.
