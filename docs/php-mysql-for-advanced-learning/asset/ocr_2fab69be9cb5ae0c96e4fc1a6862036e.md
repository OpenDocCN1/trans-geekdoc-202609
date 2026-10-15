# Subqueries in MYSQL :

A Sub query or Inner query sometime called as Nested query, is a query within another SQL query and embedded within the WHERE clause. In Simple words, a Subquery is an inner query which is placed within an outer query using different SQL clauses.

We can use Subquery anywhere mostly with select command in MYSQL enclosed within parentheses. An ORDER BY command cannot be used in a subquery, although the main query can use an ORDER BY. The GROUP BY command can be used to perform the same thing..

Example: Find list of names from a department who have more than 3 employees in the dept.

```
select name from emp where dept in(select dept from emp group by dept having count(*)>3);
```

Example 2: Display highest salary department wise and names who is taking maximum salary.

```
select emp_name from emp where salary in(select dept, max(salary) from emp group by dept);
```

```
SELECT employee_id,first_name,last_name,salary
FROM employees WHERE salary >
(SELECT AVG(SALARY) FROM employees);
```