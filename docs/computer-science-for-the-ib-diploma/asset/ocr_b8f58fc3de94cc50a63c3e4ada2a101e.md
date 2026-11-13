# Ordering data

Ordering by a single field:
SELECT * FROM Employees
ORDER BY LastName;

Ordering by a single field in ascending order:
SELECT * FROM Employees
ORDER BY LastName ASC;

Ordering by a single field in descending order:
SELECT * FROM Employees
ORDER BY LastName DESC;

Ordering by multiple fields:
SELECT * FROM Employees
ORDER BY DepartmentID, Salary DESC;

# A3.3.3 SQL update queries

| SQL statement | Explanation | Example |
| :--- | :--- | :--- |
| INSERT | Adds new records | INSERT INTO table_name (field1, field2, ...) VALUES (value1, value2, ...); |
| DELETE | Deletes records | DELETE FROM table_name WHERE condition; |
| UPDATE | Modifies records | UPDATE table_name SET field1 = value1, field2 = value2, ... WHERE condition; |

Indexed columns optimize query performance, but updating data in indexed columns may impact performance. When an update is performed for an indexed column, the index needs to be updated as well, which can slow down the operation. Also, index updates can lead to blocking other transactions that need access to a specific record. To overcome those challenges, you can batch the updates to reduce the number of times the index needs to be changed; frequently rebuild or reorganize indexes to reduce fragmentation; or use partial indexes or filtered indexes to limit the scope of the index only to the most relevant records.

# A3.3.4 SQL's aggregate functions (HL)

Aggregate functions are used to perform calculations on multiple records based on a given field. Such functions are AVERAGE, COUNT, MAX, MIN, SUM.

Aggregate functions: functions used to perform calculations on multiple records based on a given field, e.g. AVERAGE, COUNT, MAX, MIN, SUM.

| Aggregate function | Example |
| :--- | :--- |
| SUM returns the total value of a numerical field | SELECT SUM(Salary) FROM Employees; |
| COUNT returns the number of records that meet the given criteria | SELECT COUNT(EmployeeID) FROM Employees; |
| AVERAGE returns the average value of a numerical field | SELECT AVG(Salary) FROM Employees; |
| MIN returns the smallest value in a field | SELECT MIN(Salary) FROM Employees; |
| MAX returns the largest value in a field | SELECT MAX(Salary) FROM Employees; |