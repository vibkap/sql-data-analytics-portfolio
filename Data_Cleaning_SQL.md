# Data Cleaning with SQL

## Author

**Vibha Kapur**

---

# Project Overview

This project demonstrates how SQL can be used to identify and improve data quality before analysis.

Clean, accurate data is essential for reliable reporting and decision-making. The queries below identify missing values, duplicate records and inconsistent data.

---

# Skills Demonstrated

- WHERE
- IS NULL
- COUNT
- DISTINCT
- GROUP BY
- HAVING
- CASE
- ORDER BY
- Data Validation
- Data Quality Checks

---

# Business Scenario

A company has received customer and sales data from several systems.

Before creating reports, the data must be checked for quality issues.

The objective is to identify:

- Missing information
- Duplicate records
- Invalid values
- Inconsistent formatting

---

# Database Table

## Customers

| Column |
|---------|
| customer_id |
| customer_name |
| email |
| city |

---

# Business Question 1

## Find customers with missing email addresses.

```sql
SELECT *
FROM customers
WHERE email IS NULL;
```

### Insight

Missing email addresses may prevent customer communication.

---

# Business Question 2

## Count customers in each city.

```sql
SELECT city,
       COUNT(*) AS total_customers
FROM customers
GROUP BY city
ORDER BY total_customers DESC;
```

### Insight

Shows customer distribution by location.

---

# Business Question 3

## Find duplicate email addresses.

```sql
SELECT email,
       COUNT(*) AS duplicates
FROM customers
GROUP BY email
HAVING COUNT(*) > 1;
```

### Insight

Duplicate emails may indicate duplicate customer accounts.

---

# Business Question 4

## Display all unique cities.

```sql
SELECT DISTINCT city
FROM customers
ORDER BY city;
```

### Insight

Provides a clean list of customer locations.

---

# Business Question 5

## Identify customers with missing city information.

```sql
SELECT customer_name,
       city
FROM customers
WHERE city IS NULL;
```

### Insight

Missing location data reduces reporting accuracy.

---

# Business Question 6

## Categorise customer records by email availability.

```sql
SELECT customer_name,
       CASE
           WHEN email IS NULL THEN 'Missing Email'
           ELSE 'Complete'
       END AS record_status
FROM customers;
```

### Insight

Allows quick identification of incomplete records.

---

# Key Business Insights

This project demonstrates how SQL can be used to improve data quality before analysis.

The queries identify:

- Missing values
- Duplicate records
- Incomplete customer information
- Data consistency issues

Good data quality improves reporting accuracy and supports better business decisions.

---

# Tools Used

- PostgreSQL
- MySQL
- pgAdmin

---

# Skills Developed

- Data Cleaning
- Data Validation
- SQL Reporting
- Data Quality Analysis
- Business Intelligence

---

# Conclusion

Data cleaning is a critical step in every analytics project.

This project demonstrates practical SQL techniques used to identify and improve data quality before creating reports and dashboards.
