# SQL Joins Project

## Author

**Vibha Kapur**

## Project Overview

This project demonstrates my understanding of SQL joins by combining data from multiple related tables to answer common business questions.

The examples use realistic customer, order and employee datasets to show how joins are used to retrieve meaningful information for reporting and analysis.

---

# Skills Demonstrated

- INNER JOIN
- LEFT JOIN
- Table Aliases
- Primary and Foreign Keys
- Data Retrieval
- Business Reporting

---

# Business Scenario

A company stores customer information in one table and order information in another. Using SQL joins, we can combine these tables to answer business questions such as:

- Which customers have placed orders?
- Which customers have not placed orders?
- What has each customer purchased?
- Which department does each employee belong to?

---

# INNER JOIN

## Display customers and their order amounts

```sql
SELECT c.customer_name,
       o.amount
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

### What I Learned

An INNER JOIN returns only records that exist in both tables.

---

## Display customer names and order IDs

```sql
SELECT c.customer_name,
       o.order_id
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

### What I Learned

INNER JOIN is useful when analysing only customers who have placed orders.

---

## Display employees with their department information

```sql
SELECT e.employee_name,
       d.department_name,
       d.location
FROM employees e
INNER JOIN department d
ON e.department_id = d.department_id;
```

### What I Learned

Joins allow related information stored in different tables to be combined into one report.

---

# LEFT JOIN

## Display all customers, including those without orders

```sql
SELECT c.customer_name,
       o.order_id
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

### What I Learned

A LEFT JOIN returns every customer, even if they have never placed an order.

Missing values appear as NULL.

---

## Count the number of orders for each customer

```sql
SELECT c.customer_name,
       COUNT(o.order_id) AS total_orders
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
```

### What I Learned

Using a LEFT JOIN ensures customers with zero orders are still included in the results.

---

# INNER JOIN vs LEFT JOIN

| INNER JOIN | LEFT JOIN |
|------------|-----------|
| Returns only matching records | Returns all rows from the left table |
| Excludes unmatched rows | Includes unmatched rows with NULL values |
| Best for analysing existing relationships | Best for finding missing data |

---

# Business Use Cases

SQL joins are commonly used to:

- Produce customer sales reports
- Analyse employee and department information
- Create management dashboards
- Combine data from multiple business systems
- Validate relationships between datasets

---

# Summary

Through this project I strengthened my understanding of SQL joins and how they are used to combine related datasets.

I learned when to use INNER JOIN to return matching records and LEFT JOIN to include all records from the primary table, even when no related data exists.

These skills are fundamental for reporting, business intelligence and data analysis.

---

## Tools Used

- PostgreSQL
- MySQL
- pgAdmin
