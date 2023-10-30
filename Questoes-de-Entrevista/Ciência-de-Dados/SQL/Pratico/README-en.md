<p>1. Write a SQL query to retrieve all columns from a table named "employees."</p>
<pre>
SELECT * FROM employees;
</pre>
<p>2. How can you display the unique values in a column named "department" from a table named "employee_info"?</p>
<pre>
SELECT DISTINCT department FROM employee_info;
</pre>
<p>3. Write a query to find the total numer of employees in each department from a table named "employee_info".</p>
<pre>
SELECT department, COUNT(*) as total_employees
FROM employee_info
GROUP BY department;
</pre>
<p>4. Create a new table named "departments" with columns "department_id" and "department_name".</p>
<pre>
CREATE TABLE departments (
  department_id INT PRIMARY KEY,
  department_name VARCHAR(255);
</pre>
<p>5. Insert a new record into the "departments" table.</p>
<pre>
INSERT INTO departments (department_id, department_name)
VALUES (1, 'Sales');
</pre>
<p>6. Write a query to update the salary of an employee with the name "John Doe" to 60000.</p>
<pre>
UPDATE employees
SET salary = 60000
WHERE name = 'John Doe';
</pre>
<p>7. Delete all records from the "inactive_employees" table where the status is "inactive".</p>
<pre>
DELETE FROM inactive_employees
WHERE status = 'inactive';
</pre>
<p>8. Write a SQL query to retrieve the top 5 highest salaries from the "employees" table.</p>
<pre>
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 5;
</pre>
<p>9. Create a stored procedure named "GetEmployeeCount" that returns the total number of employees.</p>
<pre>
CREATE PROCEDURE GetEmployeeCount()
BEGIN
  SELECT COUNT(*) as total_employees FROM employees;
END
</pre>
<p>10. Write a SQL query to find the second highest salary from the "employees" table.</p>
<pre>
SELECT MAX(salary) AS secont_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
</pre>
