# Data Model

## Overview

The project uses a relational model in Power BI to support sales, customer, product, employee, and time analysis.

The central transaction table is `fact_sales`. Dimension tables provide descriptive attributes used to filter and group sales.

## Tables

### Fact table

- **`fact_sales`** — invoice-line-level transaction data. It includes identifiers such as `InvoiceId`, `InvoiceLineId`, `CustomerId`, and `TrackId`, as well as invoice date, unit price, quantity, and line amount.

### Dimension tables

- **`dim_customer`** — customer details, including customer name, country, and assigned support representative.
- **`dim_employee`** — employee details.
- **`dim_track`** — track attributes, including track name, album, artist, genre, media type, composer, price, duration, and file size.
- **`dim_date`** — calendar attributes used for time-based analysis, including date, year, month number, and month name.
- **`dim_playlist`** — playlist details.

### Bridge table

- **`bridge_playlist_track`** — connects playlists and tracks because a playlist can contain multiple tracks and a track can appear in multiple playlists.

## Main relationships

The sales fact table is connected to its descriptive dimensions through the relevant keys:

- `dim_customer` to `fact_sales` using `CustomerId`
- `dim_track` to `fact_sales` using `TrackId`
- `dim_date` to `fact_sales` using the invoice date
- `dim_employee` to `dim_customer` through the employee/support representative key
- `dim_playlist` to `bridge_playlist_track` and `dim_track` to `bridge_playlist_track`

The date relationship uses `dim_date[Date]` and the date-only invoice date field in `fact_sales`.

## Modeling considerations

- The sales fact table remains at invoice-line grain.
- Invoice-level totals are not summed from repeated invoice-line records.
- Playlist membership is modeled through a bridge table rather than merging playlist membership into `dim_track`. This avoids duplicating track rows when a track belongs to multiple playlists.
- The model supports filtering and analysis across customers, employees, tracks, genres, countries, and dates.

## Validation

Open the Model view in the `.pbix` file to inspect the actual relationships, cardinality, and filter direction.
