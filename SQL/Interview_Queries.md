1. **How would you find the nth highest salary in a table?**
   - This is a classic intermediate SQL question that tests your understanding of subqueries and ranking functions.
```
SELECT DISTINCT salary
FROM employees e1
WHERE (
SELECT COUNT(DISTINCT salary)
FROM employees e2
WHERE e2.salary > e1.salary
) = N - 1;
```
Replace `N` with the desired rank (e.g., 3 for the third highest salary)[5][1].

2. **What is the difference between JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN?**
- Tests your knowledge of combining tables and handling missing data:
  - `JOIN` (or `INNER JOIN`): Returns rows with matching values in both tables.
  - `LEFT JOIN`: Returns all rows from the left table, matched rows from the right table, and NULLs for non-matches.
  - `RIGHT JOIN`: Returns all rows from the right table, matched rows from the left table, and NULLs for non-matches.
  - `FULL JOIN`: Returns all rows when there is a match in either table, filling with NULLs where no match exists[5][1].

3. **How would you calculate a cumulative sum in SQL?**
- This question checks your familiarity with window functions.
```
 SELECT
employee_id,
salary,
SUM(salary) OVER (ORDER BY employee_id) AS cumulative_salary
FROM employees;
```
This computes a running total of salaries ordered by employee ID[5][1].

4. **How do you identify duplicate records in a table?**
- Tests your ability to use grouping and aggregate functions.
```
SELECT column1, column2, COUNT()
FROM table_name
GROUP BY column1, column2
HAVING COUNT() > 1;
```
Replace `column1, column2` with the columns that define a duplicate[5].

5. **Explain the concept of a window function and give examples.**
- Window functions perform calculations across a set of table rows related to the current row, without collapsing rows.
- Examples: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `SUM() OVER()`, `AVG() OVER()`
- Use case:
  ```
  SELECT
    employee_id,
    department,
    salary,
    RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS dept_salary_rank
  FROM employees;
  ```
This ranks employees by salary within each department[5][1].
