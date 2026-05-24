# 🔗 Merge and Joins in Pandas

A comprehensive guide to combining DataFrames using merge, join, and concatenation operations in Pandas. Master SQL-style joins, index-based merging, and data combination techniques.

## 📋 Table of Contents

- [Overview](#overview)
- [Types of Joins](#types-of-joins)
- [Merge vs Join vs Concat](#merge-vs-join-vs-concat)
- [Code Examples](#code-examples)
- [Common Use Cases](#common-use-cases)
- [Best Practices](#best-practices)
- [Requirements](#requirements)
- [Author](#author)

---

## 📖 Overview

Merging and joining DataFrames is essential for combining data from multiple sources. Pandas provides powerful functions to perform SQL-like operations on tabular data.

### When to Use Merge/Join?
- Combining customer data with order information
- Merging sales data with product details
- Joining employee records with department information
- Combining multiple CSV files with related columns

---

## 🎯 Types of Joins

| Join Type | Description | SQL Equivalent | Pandas Parameter |
|-----------|-------------|----------------|------------------|
| **Inner Join** | Returns only matching rows from both DataFrames | `INNER JOIN` | `how='inner'` |
| **Left Join** | Returns all rows from left DataFrame + matching rows from right | `LEFT JOIN` | `how='left'` |
| **Right Join** | Returns all rows from right DataFrame + matching rows from left | `RIGHT JOIN` | `how='right'` |
| **Outer Join** | Returns all rows from both DataFrames | `FULL OUTER JOIN` | `how='outer'` |
| **Cross Join** | Returns Cartesian product of both DataFrames | `CROSS JOIN` | `how='cross'` |

---

## 🔄 Merge vs Join vs Concat

| Function | Purpose | Key Parameter |
|----------|---------|---------------|
| `pd.merge()` | Combine DataFrames on columns or indexes | `on`, `left_on`, `right_on` |
| `df.join()` | Combine DataFrames on indexes | `how`, `lsuffix`, `rsuffix` |
| `pd.concat()` | Stack DataFrames vertically or horizontally | `axis=0` (rows), `axis=1` (columns) |

---

## 💻 Code Examples

### 1. **Inner Join** (Default)

```python
import pandas as pd

# Sample DataFrames
customers = pd.DataFrame({
    'customer_id': [1, 2, 3, 4],
    'name': ['Alice', 'Bob', 'Charlie', 'David']
})

orders = pd.DataFrame({
    'customer_id': [1, 2, 2, 5],
    'order_amount': [250, 100, 150, 300]
})

# Inner join - only customers with orders
result = pd.merge(customers, orders, on='customer_id', how='inner')
print(result)
