## **Important SQL questions**


1. Find out nth Order/Salary from the tables.
 
```sql
SELECT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET (n-1);

```

2. Find the no of output records in each join from given Table 1 & Table 2

```sql
SELECT COUNT(*)
FROM table1
JOIN table2 ON table1.id = table2.id;
```

3. YOY,MOM Growth related questions.

```sql
SELECT year, 
       (current_year_revenue - previous_year_revenue) / previous_year_revenue AS yoy_growth
FROM (
  SELECT year, 
         revenue AS current_year_revenue, 
         LAG(revenue, 1) OVER (ORDER BY year) AS previous_year_revenue
  FROM revenue_table
) AS subquery;
```

OR

```sql
WITH revenue_cte AS (
    SELECT
        year,
        revenue,
        LAG(revenue, 1) OVER (ORDER BY year) AS previous_year_revenue
    FROM
        revenue_table
)
SELECT
    year,
    (revenue - previous_year_revenue) / previous_year_revenue AS yoy_growth
FROM
    revenue_cte;
```

4. Find out Employee ,Manager Hierarchy (Self join related question) or
Employees who are earning more than managers.

```sql
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.id;

SELECT e1.name AS employee
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.id
WHERE e1.salary > e2.salary;
```

5. RANK,DENSERANK related questions

```sql
SELECT name, salary, RANK() OVER (ORDER BY salary DESC) AS rank
FROM employees;

SELECT name, salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank
FROM employees;
```

6. Some row level scanning medium to complex questions using CTE or recursive CTE, like (Missing no /Missing Item from the list etc.)

```sql
WITH MissingNumbers AS (
  SELECT n
  FROM generate_series(1, 100) n
  EXCEPT
  SELECT number FROM numbers_table
)
SELECT * FROM MissingNumbers;

WITH RECURSIVE EmployeeHierarchy AS (
  SELECT id, name, manager_id
  FROM employees
  WHERE manager_id IS NULL
  UNION ALL
  SELECT e.id, e.name, e.manager_id
  FROM employees e
  JOIN EmployeeHierarchy eh ON e.manager_id = eh.id
)
SELECT * FROM EmployeeHierarchy;
```

7. No of matches played by every team or Source to Destination flight combination using CROSS JOIN.

```sql
SELECT team1.name AS team1, team2.name AS team2
FROM teams team1
CROSS JOIN teams team2
WHERE team1.id != team2.id;

SELECT src.city AS source, dst.city AS destination
FROM cities src
CROSS JOIN cities dst;
```

8. Use window functions to perform advanced analytical tasks, such as calculating moving averages or detecting outliers.

```sql
SELECT date, 
       AVG(sales) OVER (ORDER BY date ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS moving_average
FROM sales_table;

SELECT *, 
       AVG(value) OVER () + 2 * STDDEV(value) OVER () AS upper_bound,
       AVG(value) OVER () - 2 * STDDEV(value) OVER () AS lower_bound
FROM data_table
HAVING value > upper_bound OR value < lower_bound;
```

9. Implement logic to handle hierarchical data, such as finding all descendants of a given node in a tree structure.

```sql
WITH RECURSIVE Descendants AS (
  SELECT id, name, parent_id
  FROM hierarchy_table
  WHERE id = ?
  UNION ALL
  SELECT h.id, h.name, h.parent_id
  FROM hierarchy_table h
  JOIN Descendants d ON h.parent_id = d.id
)
SELECT * FROM Descendants;
```

10.  Identify and remove duplicate records from a table.

```sql
DELETE FROM my_table
WHERE id NOT IN (
    SELECT
        MIN(id)
    FROM
        my_table
    GROUP BY
        column1, column2
    HAVING
        COUNT(*) > 1
);
```

---

## **Top 10 advanced SQL interview questions**

1. Write a query using a Common Table Expression
(CTE) to achieve a complex data transformation.

```sql
WITH SalesCTE AS (
    SELECT employee_id, SUM(sales_amount) AS total_sales
    FROM sales
    GROUP BY employee_id
),
EmployeeSalesRank AS (
    SELECT e.employee_id, e.name, s.total_sales,
           RANK() OVER (ORDER BY s.total_sales DESC) AS sales_rank
    FROM employees e
    JOIN SalesCTE s ON e.employee_id = s.employee_id
)
SELECT *
FROM EmployeeSalesRank
WHERE sales_rank <= 5;

```

2. Explain the concept of window functions and provide an example using RANK or LAG.

- Window Functions: Allow performing calculations across a set of table rows related to the current row. Examples include RANK, LAG, LEAD, etc.

```sql
SELECT employee_id, sales_amount,
       RANK() OVER (ORDER BY sales_amount DESC) AS sales_rank,
       LAG(sales_amount, 1) OVER (ORDER BY sales_amount DESC) AS previous_sales
FROM sales;

```

3. Optimize a slow-running query by identifying appropriate indexes.

```sql
-- Original slow query
SELECT * FROM orders WHERE customer_id = 123;

-- Create an index to optimize the query
CREATE INDEX idx_customer_id ON orders (customer_id);

-- Optimized query using the index
SELECT * FROM orders WHERE customer_id = 123;
```

4. Write a stored procedure that takes parameters and performs specific data manipulation tasks.

```sql
CREATE PROCEDURE UpdateEmployeeSalary (
    IN emp_id INT,
    IN new_salary DECIMAL(10, 2)
)
BEGIN
    UPDATE employees
    SET salary = new_salary
    WHERE employee_id = emp_id;
END;

CALL UpdateEmployeeSalary(1, 75000);
```

5. Explain the concept of database normalization and its benefits for data integrity.

- Database Normalization: Process of organizing data to reduce redundancy and improve data integrity. Normal forms (1NF, 2NF, 3NF) ensure that tables are structured efficiently.
- Benefits: Minimizes duplication, ensures data consistency, improves query performance, and simplifies database maintenance.

6. Write a query that finds duplicate rows in a table based on specific columns.

```sql
SELECT column1, column2, COUNT(*)
FROM table_name
GROUP BY column1, column2
HAVING COUNT(*) > 1;
```

7. Utilize temporary tables to perform multi-step data transformations within a single query.

```sql
CREATE TEMPORARY TABLE TempSales AS
SELECT employee_id, SUM(sales_amount) AS total_sales
FROM sales
GROUP BY employee_id;

CREATE TEMPORARY TABLE TempRank AS
SELECT employee_id, total_sales,
       RANK() OVER (ORDER BY total_sales DESC) AS sales_rank
FROM TempSales;

SELECT *
FROM TempRank
WHERE sales_rank <= 5;
```

8. Write a query that joins multiple tables with complex relationships (e.g., self-joins).

```sql
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.employee_id;

SELECT o.order_id, c.name AS customer_name, e.name AS employee_name
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN employees e ON o.employee_id = e.employee_id;
```

9.  Explain the differences between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN with examples.

- INNER JOIN: Returns matching rows from both tables.

```sql
SELECT * FROM A INNER JOIN B ON A.id = B.id;
```

- LEFT JOIN: Returns all rows from the left table and matched rows from the right table.

```sql
SELECT * FROM A LEFT JOIN B ON A.id = B.id;
```

- RIGHT JOIN: Returns all rows from the right table and matched rows from the left table

```sql
SELECT * FROM A RIGHT JOIN B ON A.id = B.id;
```

- FULL JOIN: Returns all rows when there is a match in either table.

```sql
SELECT * FROM A FULL OUTER JOIN B ON A.id = B.id;
```

10.  Write a query that aggregates data based on hierarchical relationships between records.

```sql
WITH RECURSIVE EmployeeHierarchy AS (
    SELECT employee_id, name, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL
    UNION ALL
    SELECT e.employee_id, e.name, e.manager_id, eh.level + 1
    FROM employees e
    JOIN EmployeeHierarchy eh ON e.manager_id = eh.employee_id
)
SELECT manager_id, COUNT(employee_id) AS total_employees
FROM EmployeeHierarchy
GROUP BY manager_id;
```
