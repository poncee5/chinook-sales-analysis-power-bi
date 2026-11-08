# DAX Measures

## Overview

The project uses DAX measures to calculate reusable business metrics for KPI cards and dashboard visuals.

The measures are organized in a dedicated `_measures` table.

## Core measures

### Total Sales

```DAX
Total Sales =
SUM(fact_sales[LineAmount])
```

Calculates revenue by summing invoice-line amounts.

### Total Quantity

```DAX
Total Quantity =
SUM(fact_sales[Quantity])
```

Calculates the total number of units/tracks purchased across invoice lines.

### Total Invoices

```DAX
Total Invoices =
DISTINCTCOUNT(fact_sales[InvoiceId])
```

Counts unique invoices rather than invoice-line rows.

### Total Customers

```DAX
Total Customers =
DISTINCTCOUNT(fact_sales[CustomerId])
```

Counts distinct customers represented in the sales fact table.

### Average Invoice Value

```DAX
Average Invoice Value =
DIVIDE([Total Sales], [Total Invoices])
```

Calculates average revenue per invoice.

### Distinct Tracks Purchased

```DAX
Distinct Tracks Purchased =
DISTINCTCOUNT(fact_sales[TrackId])
```

Counts distinct track IDs appearing in the filtered sales data. This is not the same as total quantity sold.

### Average Items per Invoice

```DAX
Average Items per Invoice =
DIVIDE([Total Quantity], [Total Invoices], 0)
```

Calculates the average quantity of items per invoice.

### Customers Managed

```DAX
Customers Managed =
DISTINCTCOUNT(dim_customer[CustomerId])
```

Counts distinct customers assigned to each employee when the employee-to-customer relationship and visual filter context are applied.

## Important interpretation notes

- **Total Quantity** counts units across invoice lines.
- **Distinct Tracks Purchased** counts unique track IDs in the current filter context.
- **Average Invoice Value** is a monetary average.
- **Average Items per Invoice** is a quantity average.
- **Customers Managed** describes customers assigned to a support representative in the dataset. It does not establish that the employee personally acquired those customers or made each sale.

## Filter context

Measures respond to report filters, slicers, and visual categories according to the model relationships. Interpret each value in the context of the filters currently applied.
