# Chinook Sales Analysis | Power BI

## Project Overview

This project focuses on analyzing the Chinook music store dataset using Microsoft Power BI.

The objective was to transform raw data into a structured data model and build an interactive dashboard to explore sales performance, customer behavior, product performance, and employee-related metrics.

## Tools & Technologies

- Microsoft Power BI
- Power Query
- DAX
- Data Modeling
- Data Visualization

## Project Workflow

### 1. Data Preparation & Cleaning

- Imported the raw Chinook dataset.
- Explored and transformed the original tables using Power Query.
- Extracted structured tables from nested JSON data.
- Removed unnecessary columns and duplicate records where appropriate.
- Applied transformations such as merging, grouping, and data type adjustments.
- Prepared fact and dimension tables for analysis.

### 2. Data Modeling

Designed a relational data model using a star-schema approach.

The model includes:

**Fact Table**
- `fact_sales`: Contains invoice-line-level sales transactions.

**Dimension Tables**
- `dim_customer`
- `dim_employee`
- `dim_track`
- `dim_date`

**Additional Tables**
- `dim_playlist`
- `bridge_playlist_track`

The model uses relationships to connect sales transactions with customers, tracks, employees, and dates. A separate bridge table handles the many-to-many relationship between playlists and tracks.

### 3. DAX Measures

Created reusable DAX measures to support the analysis, including:

- Total Sales
- Total Quantity
- Total Invoices
- Total Customers
- Average Invoice Value
- Distinct Tracks Purchased
- Average Items per Invoice
- Customers Managed by Employee

### 4. Dashboard & Business Analysis

Developed an interactive dashboard to explore several business perspectives:

- **Sales Performance:** Overall revenue and sales trends over time.
- **Product Analysis:** Revenue distribution across music genres.
- **Geographical Analysis:** Sales performance across countries.
- **Customer Analysis:** Customer distribution and purchasing behavior.
- **Employee Analysis:** Customer distribution across support representatives.
- **Time Analysis:** Monthly and yearly sales trends.

The dashboard also includes interactive filtering to explore the data from different perspectives.

## Key Skills Demonstrated

- Data Cleaning and Transformation
- Data Modeling and Relationships
- Fact and Dimension Tables
- DAX Measures
- Power Query
- Interactive Dashboard Development
- Business-Oriented Data Analysis

## Project Files

- Power BI dashboard: `PowerBI/Chinook_Sales_Analysis.pbix`
- Data preparation and modeling documentation: `Documentation/`
- Dashboard and model screenshots: `Screenshots/`

## Conclusion

This project provided hands-on experience in the end-to-end data analytics workflow, from preparing raw data and designing a relational model to developing an interactive Power BI dashboard.

The main focus was not only visualizing data, but also structuring it correctly and using it to answer meaningful business questions.
