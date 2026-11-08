# Data Cleaning & Transformation

## Overview

The Chinook dataset was imported into Microsoft Power BI and prepared in Power Query before building the data model and dashboard.

The original source data is retained separately in the repository under `data/raw/`. The transformation steps described here are performed in the Power BI file.

## Preparation workflow

1. **Imported the source data** into Power BI.
2. **Explored the source tables** to understand their structure and identify how the entities relate to one another.
3. **Expanded nested JSON data** where applicable, extracting records and lists into usable tables.
4. **Selected relevant columns** and removed fields that were not needed for the analysis.
5. **Checked data types** and assigned appropriate types to fields used for calculations and relationships.
6. **Prepared sales data** by combining invoice-level information with invoice-line details.
7. **Created a line-level sales amount** using unit price multiplied by quantity.
8. **Prepared descriptive tables** for customers, employees, tracks, albums, artists, genres, and related attributes.
9. **Prepared date information** for time-based analysis, including a date-only invoice field for the relationship with the date dimension.
10. **Reviewed duplicates and table granularity** to avoid unintentionally duplicating records.

## Sales table grain

The `fact_sales` table is designed at invoice-line level: one row represents one item on an invoice.

The line amount is calculated as:

```text
LineAmount = UnitPrice * Quantity
```

Invoice-level totals should not be summed after being repeated across invoice-line rows. The project therefore uses the line amount for sales aggregation.

## Notes

- The Power Query steps are stored in the `.pbix` file.
- The processed tables were not separately exported as CSV files for this project.
- Exact row counts and transformation details should be taken from the final Power BI file rather than assumed from this documentation.
