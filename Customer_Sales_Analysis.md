# Customer Sales Analysis using SQL

## Author

**Vibha Kapur**

---

# Project Overview

This project analyses customer purchasing behaviour using SQL.

The objective is to answer common business questions by querying customer and order data. The analysis demonstrates how SQL can be used to generate insights that support business decisions.

---

# Business Scenario

A retail company stores customer information and orders in separate tables.

Management would like answers to questions such as:

- Which customers have spent the most?
- Which customers have never placed an order?
- What is the average order value?
- Which customers have placed multiple orders?

SQL was used to retrieve, combine and summarise the data.

---

# Skills Demonstrated

- SELECT
- WHERE
- INNER JOIN
- LEFT JOIN
- GROUP BY
- HAVING
- Aggregate Functions
- Subqueries
- CTEs
- Business Reporting

---

# Database Tables

## Customers

| Column |
|---------|
| customer_id |
| customer_name |

## Orders

| Column |
|---------|
| order_id |
| customer_id |
| amount |

---

# Business Question 1

## Display all customers together with their order amounts.

```sql
SELECT c.customer_name,
       o.amount
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

### Insight

INNER JOIN returns only customers who have placed an order.

---

# Business Question 2

## Display every customer, including those who have never placed an order.

```sql
SELECT c.customer_name,
       o.order_id
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

### Insight

LEFT JOIN helps identify inactive customers.

---

# Business Question 3

## Calculate total spending for each customer.

```sql
SELECT c.customer_name,
       SUM(o.amount) AS total_spent
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_name
ORDER BY total_spent DESC;
```

### Insight

This identifies the company's highest-value customers.

---

# Business Question 4

## Find customers whose total spending exceeds £1,000.

```sql
SELECT c.customer_name,
       SUM(o.amount) AS total_spent
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_name
HAVING SUM(o.amount) > 1000;
```

### Insight

These customers could be targeted with loyalty rewards or premium offers.

---

# Business Question 5

## Calculate the average order value.

```sql
SELECT AVG(amount) AS average_order_value
FROM orders;
```

### Insight

Average order value is an important KPI for measuring customer purchasing behaviour.

---

# Business Question 6

## Find customers who have placed more than one order.

```sql
SELECT c.customer_name,
       COUNT(o.order_id) AS total_orders
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_name
HAVING COUNT(o.order_id) > 1;
```

### Insight

Frequent customers may represent loyal or repeat buyers.

---

# Business Question 7

## Find customers who have never placed an order.

```sql
SELECT customer_name
FROM customers
WHERE customer_id NOT IN
(
SELECT customer_id
FROM orders
);
```

### Insight

These customers may benefit from marketing campaigns or re-engagement activities.

---

# Business Question 8

## Rank customers by total spending.

```sql
SELECT customer_name,
       total_spent,
       RANK() OVER (ORDER BY total_spent DESC) AS spending_rank
FROM
(
SELECT c.customer_name,
       SUM(o.amount) AS total_spent
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id
GROUP BY c.customer_name
) customer_totals;
```

### Insight

Ranking highlights the highest-value customers and supports customer segmentation.

---

# Key Business Insights

Using SQL, I was able to:

- Identify top-spending customers.
- Calculate customer lifetime spending.
- Detect inactive customers.
- Measure average order value.
- Rank customers by spending.
- Support customer retention and reporting decisions.

---

# Tools Used

- PostgreSQL
- MySQL
- pgAdmin

---

# Skills Developed

- Data Analysis
- SQL Query Writing
- Business Reporting
- Customer Analytics
- Data Aggregation
- Joins
- Subqueries
- Window Functions

---

# Conclusion

This project demonstrates how SQL can be used to answer practical business questions from customer and sales data. It combines joins, aggregation, filtering and analytical functions to produce insights that support business decision-making.
