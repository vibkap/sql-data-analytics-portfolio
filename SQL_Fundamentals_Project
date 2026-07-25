# SQL Fundamentals Project

## Author

**Vibha Kapur**

## Project Overview

This project demonstrates my understanding of core SQL concepts through practical business queries.

The exercises use realistic business scenarios involving customers, products, employees and orders. They cover filtering, sorting, aggregation, joins, conditional logic, subqueries, Common Table Expressions (CTEs) and window functions.

This project forms part of my journey towards becoming a Data Analyst.

---

# Skills Demonstrated

- SELECT
- WHERE
- ORDER BY
- DISTINCT
- Aggregate Functions
- GROUP BY
- HAVING
- INNER JOIN
- LEFT JOIN
- CASE Statements
- Subqueries
- Common Table Expressions (CTEs)
- Window Functions (RANK)

---

# SQL Exercises

## 1. Display all products costing more than £50

```sql
SELECT *
FROM products
WHERE price > 50;
```

---

## 2. Display products costing less than £100

```sql
SELECT product,
       price
FROM products
WHERE price < 100;
```

---

## 3. Display products costing £300 or more

```sql
SELECT *
FROM products
WHERE price >= 300;
```

---

## 4. Display products excluding those costing £25

```sql
SELECT product
FROM products
WHERE price <> 25;
```

---

## 5. Display products priced between £50 and £500

```sql
SELECT *
FROM products
WHERE price BETWEEN 50 AND 500;
```

---

## 6. Sort products by highest price

```sql
SELECT *
FROM products
ORDER BY price DESC;
```

---

## 7. Sort products by lowest price

```sql
SELECT product,
       price
FROM products
ORDER BY price ASC;
```

---

# Aggregate Functions

## Highest product price

```sql
SELECT MAX(price)
FROM products;
```

## Lowest product price

```sql
SELECT MIN(price)
FROM products;
```

## Average product price

```sql
SELECT AVG(price)
FROM products;
```

## Number of products

```sql
SELECT COUNT(*)
FROM products;
```

---

# GROUP BY

## Number of products in each category

```sql
SELECT category,
       COUNT(*) AS total_products
FROM products
GROUP BY category;
```

---

## Average price by category

```sql
SELECT category,
       AVG(price) AS average_price
FROM products
GROUP BY category;
```

---

## Total value by category

```sql
SELECT category,
       SUM(price) AS total_price
FROM products
GROUP BY category;
```

---

# HAVING

## Categories containing more than two products

```sql
SELECT category,
       COUNT(*) AS total_products
FROM products
GROUP BY category
HAVING COUNT(*) > 2;
```

---

## Categories with an average price above £200

```sql
SELECT category,
       AVG(price) AS average_price
FROM products
GROUP BY category
HAVING AVG(price) > 200;
```

---

# INNER JOIN

```sql
SELECT c.customer_name,
       o.amount
FROM customers c
INNER JOIN orders o
ON c.customer_id = o.customer_id;
```

---

# LEFT JOIN

```sql
SELECT c.customer_name,
       o.order_id
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

---

# CASE Statement

```sql
SELECT employee_name,
       salary,
       CASE
           WHEN salary > 80000 THEN 'Top'
           WHEN salary BETWEEN 50000 AND 80000 THEN 'Mid'
           ELSE 'Low'
       END AS salary_level
FROM employees;
```

---

# Subqueries

## Employees earning above the average salary

```sql
SELECT employee_name,
       salary
FROM employees
WHERE salary >
(
SELECT AVG(salary)
FROM employees
);
```

---

## Employee(s) earning the highest salary

```sql
SELECT employee_name,
       salary
FROM employees
WHERE salary =
(
SELECT MAX(salary)
FROM employees
);
```

---

## Customers who have placed an order

```sql
SELECT customer_id,
       customer_name
FROM customers
WHERE customer_id IN
(
SELECT customer_id
FROM orders
);
```

---

## Customers spending more than £1000

```sql
SELECT customer_id,
       customer_name
FROM customers
WHERE customer_id IN
(
SELECT customer_id
FROM orders
GROUP BY customer_id
HAVING SUM(amount) > 1000
);
```

---

# Common Table Expression (CTE)

```sql
WITH customer_sales AS
(
SELECT customer_id,
       SUM(amount) AS total_amount
FROM orders
GROUP BY customer_id
)
SELECT *
FROM customer_sales
WHERE total_amount > 500;
```

---

# Window Function

## Rank employees by salary within each department

```sql
SELECT employee_name,
       department,
       salary,
       RANK() OVER
       (
       PARTITION BY department
       ORDER BY salary DESC
       ) AS salary_rank
FROM employees;
```

---

# What I Learned

Throughout this project I developed practical SQL skills by solving business-focused problems using realistic datasets.

I gained confidence writing queries to filter, sort and aggregate data, combine multiple tables using joins, summarise information using GROUP BY and HAVING, apply conditional logic with CASE statements, retrieve information using subqueries, organise complex queries with Common Table Expressions (CTEs) and rank results using window functions.

These exercises strengthened my understanding of how SQL can be used to analyse data, answer business questions and support data-driven decision making.

---

## Tools Used

- PostgreSQL
- MySQL
- pgAdmin

---

## Next Steps

- Advanced SQL
- Power BI Dashboards
- Excel Dashboard Projects
- Real Business Case Studies
- Data Cleaning Projects
