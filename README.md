# 🔍 Data Quality Audit

> Simulated a real-world Data Quality Audit on 250 transactional records, identifying a **4% row-level error rate** across revenue mismatches, duplicate IDs, invalid product references, missing values, and non-standard formats.

---

## 📌 Project Overview

This project simulates the role of a **Data Quality Analyst** at an e-commerce/retail company. Given a raw transactional dataset of 250 orders, the task was to systematically identify, document, and recommend fixes for all data quality issues — following a structured Issue → Impact → Recommendation → Action Taken framework.

**Tools Used:** Microsoft Excel (XLOOKUP, IF, ISNUMBER, TRIM, SUBSTITUTE, Pivot Tables)
**Dataset Size:** 250 order records | 9 columns
**Skills Demonstrated:** Data Validation, Formula-Based QA, Outlier Detection, Error Rate Calculation, Stakeholder Reporting

---

## 📁 Workbook Structure

| Sheet | Purpose |
|---|---|
| `Raw_Data` | Original unmodified dataset |
| `Tasks` | Full Issue-Impact-Recommendation-Action for all 13 tasks |
| `Cleaned_Data` | Validation layer with formula-based QA checks |
| `Product_Master` | Reference table for Product_ID validation |
| `Pivot_Tables` | Revenue by Country and Orders by Status summaries |
| `QA_Findings` | Executive summary, risk table, and strategic recommendations |

---

## 📊 Dataset Description

| Column | Description |
|---|---|
| Order_ID | Unique transaction identifier |
| Customer_ID | Customer reference |
| Order_Date | Date of order placement |
| Product_ID | Product reference (validated against Product_Master) |
| Quantity | Units ordered |
| Unit_Price | Price per unit |
| Total_Revenue | Should equal Quantity × Unit_Price |
| Country | Country of order |
| Status | Order status (Completed / Pending / Cancelled) |

---

## 🧪 QA Framework — Validation Checks Applied

The `Cleaned_Data` sheet adds 6 formula-based validation columns to every row:

| Check Column | Formula Logic | Purpose |
|---|---|---|
| `Revenue_Check` | `IF(Total_Revenue <> Qty × Price, "Mismatch", "Ok")` | Detect revenue calculation errors |
| `Date_Check` | `ISNUMBER(Order_Date)` | Verify date is stored as numeric, not text |
| `Country_Validation` | `XLOOKUP(UPPER(SUBSTITUTE(TRIM(Country)...)))` | Standardize and validate country values |
| `Order_Validation` | `IF(Status IN allowed set, "Valid", "Invalid")` | Enforce status field integrity |
| `Product_Validation` | `XLOOKUP(Product_ID, Product_Master)` | Validate against master reference |
| `Row_Issues` | `IF(any check fails, "Problem", "Clean")` | Row-level error flag |

---

## 🔎 Findings Summary

### Executive Summary

| Metric | Value |
|---|---|
| Total Records Analyzed | 250 |
| Unique Problematic Rows | 10 |
| Overall Row-Level Error Rate | **4%** |
| Quantity Column Error Rate | **0.8%** |
| Overall Assessment | Moderate data integrity issues requiring validation before reporting |

---

### High-Level Issues by Risk

| Category | Records Affected | Risk Level |
|---|---|---|
| Duplicate Order_ID | 4 | 🔴 High |
| Revenue Mismatch | 6 | 🔴 High |
| Invalid Product_ID | 2 | 🔴 High |
| Missing Critical Fields | 3 | 🔴 High |
| Invalid Date Format | 249 | 🟡 Medium |
| Negative Quantity | 2 | 🟡 Medium |

---

### Detailed Task Findings

**1. Duplicate Order_IDs**
Order_ID 1006 and 1016 each appear in multiple records with conflicting customer, date, quantity, and country values. This compromises transaction uniqueness and may cause incorrect revenue aggregation.

**2. Revenue Mismatches**
6 records where Total_Revenue ≠ Quantity × Unit_Price. Leads to financial misstatement if used in reporting without validation.

**3. Negative Quantity Values**
2 records contain negative quantity entries. May indicate returns or data entry errors — requires business rule clarification before treatment.

**4. Missing Critical Fields**
3 records detected with missing values: 1 Order_Date and 2 Unit_Price fields. Leads to revenue misstatement and incomplete sales reporting.

**5. Invalid Date Format**
249 records had Order_Date stored as text instead of a proper date format. Causes errors in date-based filtering, grouping, and time-series analysis.

**6. Inconsistent Country Values**
Country column contained "india", "U.S.A", "Uk", and values with trailing spaces. Fixed using TRIM and UPPER(SUBSTITUTE()) mapping logic to ensure uniform formatting.

**7. Invalid Status Values**
2 records contain status values outside the allowed set — "Done" and "Processing" instead of Completed/Pending/Cancelled. Causes workflow misclassification in reporting.

**8. Invalid Product_IDs**
2 records reference Product_IDs not found in Product_Master. Breaks referential integrity and causes incorrect product-level revenue aggregation.

**9. Unique Problematic Rows**
10 unique rows identified with at least one data quality issue after deduplication across all checks.

**10. Overall Error Rate**
4% of all transactions contain at least one data quality issue affecting financial, product, or operational reporting.

**11. Quantity Column Error Rate**
0.8% of records contain invalid (negative) quantity values.

---

## 📈 Pivot Table Summaries

### Revenue by Country

| Country | Count of Revenue |
|---|---|
| India | $1,093,902 |
| UK | $923,919 |
| Canada | $865,894 |
| USA | $751,564 |
| **Grand Total** | **$3,635,279** |

### Orders by Status

| Status | Count | Valid? |
|---|---|---|
| Cancelled | 97 | ✅ |
| Pending | 77 | ✅ |
| Completed | 74 | ✅ |
| Done | 1 | ❌ Invalid |
| Processing | 1 | ❌ Invalid |

---

## 🛠️ Data Quality Score (DAMA Framework)

| Dimension | Score | Notes |
|---|---|---|
| Completeness | 98.8% | 3 missing fields out of 250 records |
| Accuracy | 97.6% | 6 revenue mismatches |
| Consistency | 99.2% | 2 invalid status + country formatting issues |
| Uniqueness | 99.2% | 2 duplicate Order_IDs |
| **Overall** | **~96%** | 10 unique problematic rows / 250 total |

---

## ✅ Strategic Recommendations

1. Implement automated validation controls at the data ingestion stage to catch errors before they enter the system
2. Enforce referential integrity between transactional data and master reference tables (Product_Master)
3. Apply mandatory field validation for critical attributes — Order_Date, Unit_Price, Quantity
4. Implement revenue reconciliation logic to auto-flag mismatches at entry
5. Standardize categorical fields (Country, Status) using controlled dropdown lists or reference mapping to prevent free-text inconsistencies

---

## 💡 Key Takeaway

This project demonstrates a complete Data QA workflow — from raw data ingestion through formula-based validation, error quantification, and structured stakeholder reporting. The approach mirrors real-world data analyst responsibilities in operations, finance, and reporting teams.

---

## 🔗 Connect
**LinkedIn:** [linkedin.com/in/guptaharsh1401](https://linkedin.com/in/guptaharsh1401)
**GitHub:** [github.com/Harsh1887](https://github.com/Harsh1887)
