# Bookstore-Inventory-
# Bookstore Inventory and Analytics System

A Python-based system to manage a bookstore's inventory, analyze sales data,
and visualize trends. Built using Control Structures, Arrays, Object-Oriented
Programming, NumPy, Pandas, and Matplotlib/Seaborn.

## Project Structure

```
.
├── bookstore_system.py   # Main application (Bookstore class + CLI)
├── inventory.csv          # Sample inventory dataset (Title, Author, Genre, Price, Quantity)
├── sales.csv               # Sample sales dataset (Date, Title, Quantity Sold, Total Revenue)
└── README.md               # This file
```

## Features

- **Inventory Management**: add, update, and validate books (control structures ensure
  price/quantity are always valid).
- **`Bookstore` class (OOP)**: `add_book`, `update_inventory`, `record_sale`,
  `generate_report`, plus analytics/visualization methods.
- **Sales Analysis (NumPy + Pandas)**: total revenue, average price, monthly
  sales growth rate, best-selling books, revenue by genre/author.
- **Data Visualization (Matplotlib + Seaborn)**:
  - Bar chart — total sales by genre
  - Line graph — monthly sales trend
  - Pie chart — revenue share by genre
  - Heatmap — correlation between price and sales volume

## Setup Instructions

1. **Requirements**: Python 3.9+ and the following packages:
   ```
   pip install numpy pandas matplotlib seaborn
   ```

2. **Run the program** (make sure `inventory.csv` and `sales.csv` are in the
   same folder as `bookstore_system.py`):
   ```
   python bookstore_system.py
   ```

3. **Using the menu**: the program launches an interactive CLI —
   ```
   1. Add a new book
   2. Update inventory quantity
   3. Record a sale
   4. Generate summary report
   5. Generate all visualizations (charts saved as PNG)
   6. Show best-selling books
   7. Save changes to CSV
   8. Exit
   ```
   Choose option `5` to generate all four charts as PNG files in the same
   directory. Choose option `7` (or `y` when exiting) to persist any
   inventory/sales changes back to the CSV files.

## Dataset Notes

- `inventory.csv` — 25 sample books across 10 genres (Fiction, Romance,
  Technology, Fantasy, Mystery, Adventure, Non-Fiction, Science, Poetry,
  Historical), with randomized prices and stock quantities.
- `sales.csv` — ~823 synthetic daily sales transactions spanning 6 months
  (March–September 2026), generated with genre-weighted random sales volume
  so that visualizations show realistic trends and variation.

Both datasets were generated programmatically (with the help of AI, using
NumPy's random generator with a fixed seed for reproducibility) as sample
data for testing the system — you can replace them with real bookstore data
using the same column structure.

## Notes for Reviewers

- All user inputs (price, quantity, titles) are validated before being
  applied; invalid input never corrupts the DataFrames.
- Missing/invalid values in the CSVs are handled during loading (`_load_inventory`,
  `_load_sales`) via `pd.to_numeric(..., errors="coerce")` and `dropna`.
- Code is organized into a single `Bookstore` class for modularity, with a
  thin CLI (`run_cli`) layered on top for interaction.
