
statement. This is similar to how you define it in a SELECT statement where you list multiple SELECT statements together separated with commas.

If you want to see all the customers and their customer numbers in ascending order and also their names, you can use a statement similar to this:

To actually see what the results look like before running a query, you can use a tool called HeidiSQL.

The ORDER BY is usually the very first statement, but you can use it at any point in your query. The keyword "ORDER" itself can be used before or after the table name. The ORDER BY clause is not required to use the GROUP BY clause.

The ORDER BY keyword is used in queries, not in the CREATE TABLE statement. The results are ordered based on the columns that you specify, and they will remain sorted after the execution of the query unless you follow it with an additional query that inserts or updates data in that table.

## SQL Insert Into Clause

Insert Into is a clause that does not have any outcome statements and instead performs the action of inserting specified rows from one table into another table. The clause has two parts, the first part specifies the source table, and the second part specifies the destination table.

Fields can be inserted or appended with the columns that are in the target table. If a field is not specified and it is in the source table, then it will be ignored, and that field will not appear in the target table.

For example, if a source table has a column named A with five rows and another column B with two rows of data, and if we insert this into another table that has three columns, then there will be no columns defined after our select statement.

Instead of setting up a new table and copying all the data into it, use a select statement to extend your existing table. Then insert the results of your select statement into the existing table. This is often easier than inserting multiple rows into one table.

If you want to add a new column to an existing table, use the append clause of this clause.

If you want to delete a column from an existing table, use the delete clause of this clause.

The insert clause can be used in combination with the select, update, and delete clauses for adding new columns to existing tables.

To insert into a table, you need to specify the source and destination tables. The source (input) table can be a local or a global temporary table. The destination table must be a base table.

## The UPDATE Statement

The UPDATE statement is a control statement that updates the values of the specified columns in a table. It is similar to INSERT and DELETE statements, except that it does not actually insert or delete rows from the table. The UPDATE statement changes only what is contained in the specified columns for an individual row at a time.

The UPDATE statement cannot be used to update the same column more than once within a single UPDATE statement. For example, you can use a WHERE clause to change the salary of all employees who earn less than $10,000 per year. The following statement is not legal:

Once an expression is computed in an UPDATE statement, it cannot be redefined within the same UPDATE statement (through the use of SET or new expressions).

The UPDATE statement can be executed under either of the following two circumstances:

A single UPDATE statement can update multiple rows from a table. This is called a multi-row UPDATE statement. The number of rows in the table that this type of UPDATE statement affects can be as large as one million; however, there are some limitations.

In this kind of UPDATE statement, the WHERE clause begins with the table selector and then consists of a selection of key columns from which individual rows are selected for updating. This selection is called a selection list.

The first column in the selection list always is the column identifier (also called a table name or primary key) for the table being updated. The second and any subsequent columns in the selection list are referred to as referring columns; these specify individual rows to be selected.

In a multi-row UPDATE statement, the SELECT statement is followed by an ORDER BY clause that specifies the sort order for all the rows to be updated. The UPDATE statement then contains an expression that is evaluated for each row in the table being updated. Each of these expressions is assigned to one of the referring columns specified in the SELECT list. If a row meets all these criteria, then its values are updated; otherwise, they are left unchanged. The value of the primary key column is always updated.

Important: Each of the SELECT and ORDER BY clauses has an implicit ORDER BY on the entire table being updated so that sorting is based on the entire table's order. For example, in a multi-row UPDATE statement that updates all columns sorted by the first name, you must use parentheses to explicitly force this ordering on each particular row to be updated.

## The DELETE Statement

In a database, the DELETE statement can be used to delete data from any table or view. However, you cannot use it to delete data from a table when there is a foreign key that references the table. When using the DELETE command, you should specify all columns that you want to remove from a particular database table. If you do not specify which columns should be deleted, all of the database table's columns will be removed.

The DELETE statement has the following syntax:

```
DELETE <table_name> [WHERE <condition>] [FROM <the_starting_point>] [WITH <options>]
```

This means that the DELETE statement selects columns and removes rows satisfying certain conditions.

Generally, you can use the DELETE command to delete data from a table or view.

- 1: Suppose that you have a table in your database named Resume. The Resume table has three columns named Emp_ID, Name, and Current_Salary. You can use the following SQL commands to delete all rows of the Resume table that have an Emp_ID value of 100:

```
DELETE FROM Resume WHERE Emp_ID = 100
```

- 2: Suppose that you want to delete all rows in a table named Department that has an Emp_ID value of 100. You can use the following SQL command to delete those rows:

```
DELETE FROM Department WHERE Emp_ID = 100
```

- 3: Suppose that you have a table in your database named Employees. The Employees table has four columns named Emp_ID, First_Name, Last_Name, and Salary. Suppose that there are several rows in the Employees table that you want to delete. You can use the following SQL command to delete those rows:

```
DELETE FROM Employees WHERE Emp_ID IN (SELECT Emp_ID FROM Employees WHERE First_Name = 'Chris' OR Last_Name = 'Pederson')
```

- 4: Suppose that you have an Employees table in your database where one of the columns of the table is Project_ID. The Project_ID column has a foreign key reference to a table named Projects. The Projects table has several rows in the table, each of which has an Emp_ID value of 100. You can use the following SQL command to delete all rows in the Employees table that have an Emp_ID value of 100:

```
DELETE FROM Employees WHERE Emp_ID = 100 AND Project_ID IN (SELECT DISTINCT Project_ID FROM Projects WHERE Name = 'New Products')
```

## TOP, ROWNUM, LIMIT Clause

In this section, we are going to focus on the TOP, ROWNUM, LIMIT Clauses and look at some of their uses and limitations. We’re going to start with the TOP Clause and end with a look at the LIMIT Clause.

### The TOP Clause

The TOP Clause helps ensure that output is limited to specific values. We will start out by explaining this clause and then explore some of its uses and limitations before moving on to look at the ROWNUM and LIMIT Clauses.

The TOP clause is used to limit the number of rows sent back from a query. It determines the order of the output from an SQL statement and specifies how many rows are sent back. A TOP Clause can be used with any clause that generates rows (where, select, order by, and group by).

A TOP clause only evaluates when all rows have been fetched from a table or when those rows don’t fulfill a condition (e.g., if the limit is less than the total number of records in a table).

There is a different syntax for the TOP Clause that comes from SQL-92 and SQL:2003. All of these forms will be covered here below.

Now, let’s take a look at some examples so we can get some practice. The first example will just show us how to use the TOP Clause with a SELECT statement. In this example, if there are more than five rows in the table, only five will be returned.

```
select * from newstaffpartition where staffid > 10 order by staffid
TOP 5 OF NEWSTAFFPARTITION WHERE STAFFID > 10 ORDER BY STAFFID
```

If we want to get a combination of many values, the TOP Clause can help.

```
select * from newstaffpartition order by staffid, Lastname, firstname, age where staffid > 10 order by name
TOP 5 OF NEWSTAFFPARTITION ORDER BY STAFFID, LASTNAME, FIRSTNAME, AGE WHERE STAFFID > 10 ORDER BY NAME
```

Using the TOP Clause with a GROUP BY statement is similar to using it with a SELECT statement. The example below will generate an output that only shows the top five employees.

```
select Lastname, firstname, age from newstaffpartition
GROUP BY LASTNAME, FIRSTNAME, AGE
TOP 5 OF NEWSTAFFPARTITION GROUP BY LASTNAME, FIRSTNAME, AGE
```

It’s also possible to combine TOP with both ORDER BY and LIMIT. These next three examples will show how to get results for the top five people in the list (based on employment date), but only information for the last five people who were hired by year.

```
select * from newstaffpartition group by Lastname, firstname
GROUP BY LASTNAME, FIRSTNAME LIMIT 5
```

```
TOP 5 OF NEWSTAFFPARTITION GROUP BY LASTNAME, FIRSTNAME LIMIT 5
```

Similar to the previous examples, you can use TOP with both a SELECT and a GROUP BY. The two following examples show how to get results for the top five employees (by the last name) or the top five by employment date (by the last name).
