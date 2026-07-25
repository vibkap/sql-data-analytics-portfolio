# HR Employee Analytics using SQL

## Author

**Vibha Kapur**

---

# Project Overview

This project analyses employee salary and department data using SQL to produce insights that support workforce planning and business decision-making.

The project demonstrates the use of SQL for reporting, ranking, categorisation and departmental analysis.

---

# Business Scenario

A company would like to understand employee salaries across departments.

Management wants to answer questions such as:

- Which employees earn the highest salaries?
- What is the average salary by department?
- Which departments have the most employees?
- Who earns above the company average?
- Which are the top two highest-paid employees in each department?

---

# Skills Demonstrated

- SELECT
- WHERE
- GROUP BY
- HAVING
- CASE
- Aggregate Functions
- Window Functions
- RANK()
- CTEs
- Subqueries

---

# Database Table

## Employees

| Column |
|---------|
| employee_id |
| employee_name |
| department |
| salary |

---

# Business Question 1

## Display all employees ordered by salary.

```sql
SELECT employee_name,
       department,
       salary
FROM employees
ORDER BY salary DESC;
```

### Insight

Provides a company-wide salary ranking.

---

# Business Question 2

## Find employees earning above the company average salary.

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

### Insight

Identifies higher-paid employees relative to the company average.

---

# Business Question 3

## Calculate the average salary for each department.

```sql
SELECT department,
       AVG(salary) AS average_salary
FROM employees
GROUP BY department;
```

### Insight

Highlights departments with higher average salaries.

---

# Business Question 4

## Count employees in each department.

```sql
SELECT department,
       COUNT(employee_id) AS total_employees
FROM employees
GROUP BY department
ORDER BY total_employees DESC;
```

### Insight

Shows the size of each department.

---

# Business Question 5

## Categorise salaries.

```sql
SELECT employee_name,
       salary,
       CASE
           WHEN salary > 80000 THEN 'High'
           WHEN salary BETWEEN 50000 AND 80000 THEN 'Medium'
           ELSE 'Low'
       END AS salary_band
FROM employees;
```

### Insight

Groups employees into salary bands for reporting.

---

# Business Question 6

## Rank salaries within each department.

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

### Insight

Ranks employees within their own department.

---

# Business Question 7

## Display the top two earners in every department.

```sql
SELECT employee_name,
       department,
       salary,
       salary_rank
FROM
(
SELECT employee_name,
       department,
       salary,
       RANK() OVER
(
PARTITION BY department
ORDER BY salary DESC
) AS salary_rank
FROM employees
) ranked_employees
WHERE salary_rank <= 2;
```

### Insight

Useful for succession planning and leadership reporting.

---

# Business Question 8

## Using a CTE, display departments where the average salary exceeds £60,000.

```sql
WITH department_salary AS
(
SELECT department,
       AVG(salary) AS average_salary
FROM employees
GROUP BY department
)

SELECT *
FROM department_salary
WHERE average_salary > 60000;
```

### Insight

Highlights departments with higher payroll costs.

---

# Key Business Insights

This analysis enables managers to:

- Compare departmental salary levels.
- Identify top performers.
- Understand workforce distribution.
- Analyse salary trends.
- Support budgeting and workforce planning.

---

# Tools Used

- PostgreSQL
- MySQL
- pgAdmin

---

# Skills Developed

- SQL Reporting
- Data Analysis
- Window Functions
- Business Intelligence
- HR Analytics
- CTEs
- Subqueries
- CASE Statements

---

# Conclusion

This project demonstrates how SQL can be applied to HR data to generate meaningful insights for workforce analysis and business reporting.
