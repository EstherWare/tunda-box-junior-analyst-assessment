# Tunda Box — Junior Data Analyst Assessment


**Author:** Esther Wambui Kafuko

**Course & Cohort:** PLP Data Analytics (Cohort 7)  

**Notebook File:** [`[tunda_box_assessment.ipynb](https://colab.research.google.com/drive/1e7-Hiv70XtQosCI77oaZBEWfekGWIhvE?usp=sharing)`](./[tunda_box_assessment.ipynb](https://colab.research.google.com/drive/1e7-Hiv70XtQosCI77oaZBEWfekGWIhvE?usp=sharing))  
**Drive Reference Document: ** ( https://docs.google.com/document/d/1_0zZ4j2TrdIouSZGNnaR-vTAcOBhMFz4wDNb-2bgOuE/edit?usp=sharing )

---

## 1. Project Overview & Business Problem
Tunda Box is a Nairobi-based fresh fruit and vegetable delivery service. This project conducts a end-to-end data audit, statistical evaluation, and strategic business analysis across two primary datasets: `customers` (10 records) and `orders` (21 records). 

The primary business objectives are:
1. **Data Cleaning & Auditing:** Identify and resolve referential integrity failures, casing inconsistencies, duplicate entries, missing values, and extreme outliers across transactional data.
2. **Key Performance Metrics:** Compute order counts by status, cleaned revenue by city, non-ordering customer segments, repeat purchase rates (80%), and month-on-month growth.
3. **Statistical & Business Case Evaluation:** Diagnose a site-wide conversion drop from 5.2% in September to 4.3% in October using Simpson's Paradox, and evaluate A/B test results for platform recommendations.

---

## 2. Technical Stack & Methodology
- **Language & Runtime:** Python 3 (Google Colab environment)
- **Data Structures:** Core Python (`dict`, `list`, `set`, tuples) without third-party data manipulation dependencies (e.g., pandas/NumPy) for foundational logic verification.
- **Data Quality Logic:** String normalization (`.strip().title()`), dictionary aggregation (`.get()`), and tuple slicing for growth calculations.

---

## 3. Top Key Findings

1. **Traffic Mix Shift Driven by Simpson's Paradox (Part 5)**
   - While overall site conversion fell from **5.2% to 4.3%**, individual channel conversions actually *increased*: **Organic** rose from **6.0% to 6.1%**, and **Paid Social** rose from **2.0% to 2.1%**. 
   - The overall drop is a mathematical effect caused by scaling Paid Social (a lower-converting top-of-funnel channel) from 20% to 44.1% of total site sessions, which generated **215% more orders** overall.

2. **Strong Customer Loyalty (Part 2)**
   - Out of 10 registered customers, **8 have placed 2 or more orders**, representing an **80.0% Repeat Purchase Rate**. 
   - Two registered customers (ID `109` in Eldoret and ID `110` in Kisumu) have placed zero orders to date.

3. **Data Quality & Revenue Distortions (Part 3)**
   - The dataset contained severe anomalies, including an extreme outlier order (#1013 for **KES 185,000**), duplicate entries (#1006), invalid referential integrity (Customer ID `999`), and missing values (#1009). 
   - Using the **median order value (KES 2,450)** provides a far more accurate representation of typical customer spending than the mean, which is distorted to over KES 11,000 by the single outlier.

---

## 4. Summary of Analysis & Thought Process

### Part 1: Background & Experience
- Documented data analysis background, tools proficiency (SQL, Python, Excel), and approach to resolving data ambiguities with stakeholders.

### Part 2: Python Data Operations
- **Status Breakdown:** Completed (17), Cancelled (2), Refunded (2).
- **Cleaned Revenue by City:** Successfully cleaned city strings (e.g., `"nairobi"`, `"Nairobi`). Nairobi generated KES 20,650 in completed orders.
- **Growth Tracking:** Computed baseline completed revenue for June (KES 9,000), July (KES 6,800), August (KES 192,000, including outlier), and September (KES 10,300).

### Part 3: Data Audit & Spreadsheet Logic
- Formulated `SUMIFS` formulas for completed M-Pesa revenue (`=SUMIFS(E:E, D:D, "completed", F:F, "M-Pesa")`) and `XLOOKUP`/`VLOOKUP` for customer city integration.
- Standardized data quality remediation rules for orphan rows, missing payment amounts, and string syntax errors.

### Part 4: Statistical Evaluation & A/B Testing
- Explained p-values and correlation vs. causation in non-technical business language.
- Advised against launching the new checkout redesign (p = 0.33), identifying that the 10-conversion lift across 1,000 users was statistically insignificant due to an underpowered sample size.

### Part 5: Executive Business Recommendation
- **Recommendation:** Do not pause Paid Social. Pausing the channel would halt a tripling of order volume (+215%) from a channel whose conversion rate actually improved. Optimization efforts should target landing page conversion, audience targeting, and ROAS rather than pausing spend.

---

## 5. How to Run the Code

1. Open the [`tunda_box_assessment.ipynb`](./tunda_box_assessment.ipynb) file in **Google Colab**.
2. Select **Runtime → Restart session and run all** (or press `Ctrl + F9` / `Cmd + F9`).
3. View the printed diagnostic reports and structured outputs in each cell.
