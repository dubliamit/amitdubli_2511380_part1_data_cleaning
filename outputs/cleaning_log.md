
# Data Cleaning Log

## Project Summary
- Source file: raw_orders.xlsx
- Output file: cleaned_orders.xlsx
- Total records after cleaning: 912

---

## 1. Issues Found

The following data quality issues were identified:

- Missing values in region, ship_mode, discount and date fields.
- Mixed date formats in order_date and ship_date.
- Leading/trailing spaces and inconsistent text formatting.
- Inconsistent capitalization in categorical columns.
- Invalid or unusual discount values.
- Exact duplicate records.
- Duplicate order IDs with conflicting information.
- Ship dates earlier than order dates.
- Cancelled, refunded and failed payment transactions.

---

## 2. Cleaning Actions Performed

### Text Fields
- Removed leading and trailing spaces.
- Replaced multiple spaces with a single space.
- Removed unwanted special characters where applicable.
- Standardized text case.
- Standardized category, segment, ship mode and status values.

### Date Fields
- Converted order_date and ship_date to a consistent date format.
- Flagged missing and invalid dates.
- Calculated shipping_delay_days.
- Flagged records where ship_date occurred before order_date.

### Missing Values
- Missing region values were replaced with 'Unknown'.
- Missing ship_mode values were replaced with 'Unknown'.
- Missing discount values were replaced with 0 only when other sales fields were valid.

### Duplicate Handling
- Removed exact duplicate rows.
- Retained duplicate order IDs with conflicting information.
- Flagged conflicting duplicate records for manual review.

### Calculated Columns
Created the following columns:

- cleaned_discount
- calculated_sales
- calculated_profit
- profit_margin
- shipping_delay_days
- order_month
- order_year
- data_quality_flag

---

## 3. Business Rules Applied

- Missing region → Filled with 'Unknown'
- Missing ship mode → Filled with 'Unknown'
- Missing discount → Replaced with 0 only when other sales fields were complete
- Negative discounts → Flagged as invalid
- Discounts above allowed range → Flagged as invalid
- Ship date earlier than order date → Flagged as invalid
- Cancelled orders excluded from completed sales summaries
- Failed payment records excluded from completed sales summaries
- Refunded orders summarized separately
- Conflicting duplicate order IDs retained and flagged

---

## 4. Assumptions Made

- Discounts are stored as decimal values between 0 and 1.
- Missing region and ship mode values are represented as 'Unknown'.
- Shipping delay is calculated as:
  Ship Date - Order Date
- Profit is calculated as:
  Calculated Sales - Cost
- Profit margin is calculated as:
  Calculated Profit / Calculated Sales
- Invalid numeric values were converted to missing values where necessary.

---

## 5. Records Removed

- Exact duplicate rows removed: 20

---

## 6. Records Flagged

- Conflicting duplicate records: 24
- Invalid discount records: 15
- Invalid shipping records: 91
- Records with missing region: 25
- Records with missing ship mode: 21

---

## 7. Limitations

- Ambiguous date formats may require manual verification.
- Similar category names not present in the mapping dictionary may remain inconsistent.
- Business validation was limited to the rules provided.
- Flagged records should be manually reviewed before production use.

---

## 8. Output Files Generated

- cleaned_orders.xlsx
- data_quality_report.xlsx
- pivot_summary.xlsx
- cleaning_log.md

---

Cleaning completed successfully.
