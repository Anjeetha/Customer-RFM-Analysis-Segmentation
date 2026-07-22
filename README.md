# 📊 Commerce Customer RFM Analysis & Segmentation

An end-to-end Python data analytics project utilizing **RFM (Recency, Frequency, Monetary)** methodology to segment over **500,000+ e-commerce transaction records**. This project cleans raw transactional data and categorizes customers into distinct **Loyalty Badges** (*Platinum*, *Gold*, *Silver*, *Bronze*) to drive data-informed retention strategies and marketing decisions.

## 📌 Executive Summary

Understanding customer buying patterns is critical for optimizing marketing efforts and maximizing Customer Lifetime Value (CLV). This project processes e-commerce purchase logs, handles missing values, cleans duplicate records, typecasts numeric and datetime fields, and applies quantile-based scoring across three core metrics:

* **Recency:** Days elapsed since the customer's last purchase relative to the billing closing date (`2017-12-20`).
* **Frequency:** Total count of transactions per unique customer.
* **Monetary:** Total gross transaction value accumulated by the customer.

## 🛠️ Tech Stack & Libraries

* **Language:** Python 3.x
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `seaborn`, `matplotlib`
* **Date Parsing:** `datetime`
* **Environment:** Google Colab / Jupyter Notebook

## 📈 Pipeline & Methodology

1. **Data Cleaning & Typecasting:**
   * Loaded source data using `ISO-8859-1` character encoding.
   * Dropped missing `CustomerID` records (`25.3%` missing handling).
   * Removed 1,330 duplicate transaction rows.
   * Typecasted `CustomerID` and `InvoiceNo` to integers, and converted date strings into `datetime` objects.
2. **RFM Metric Aggregation:**
   * Calculated recency against a fixed baseline date (`2017-12-20`).
   * Aggregated `Recency`, `Frequency`, and `Monetory` values grouped by `CustomerID`.
3. **Quantile Scoring (`R_Rank`, `F_Rank`, `M_Rank`):**
   * Derived statistical quantiles (`0.25`, `0.50`, `0.75`) for parameter thresholds.
   * Applied custom scoring functions to assign rank scores (1 to 4).
   * Computed a composite `LoyalityScore` per customer.
4. **Loyalty Badge Segmentation:**
   * Used `pd.qcut()` to bin composite scores into 4 distinct segments:
     * 🥇 **Platinum:** Most frequent, recent, and high-value shoppers.
     * 🥈 **Gold:** High-value repeat customers.
     * 🥉 **Silver:** Moderate engagement buyers.
     * 🏷️ **Bronze:** Low frequency/at-risk customers.

## 📊 Segment Distribution

| Loyalty Badge | Customer Count |
| :--- | :--- |
| **Platinum** | 1,313 |
| **Gold** | 1,280 |
| **Silver** | 966 |
| **Bronze** | 790 |
