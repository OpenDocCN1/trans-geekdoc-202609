# Query:

Select * from users right join rec on users.uid=rec.uid;

This would return all rows from the **rec** table and only those rows from the **users** table where the joined fields are equal.

# Assignments for the practice

+   1. Write a SQL statement to prepare a list with Customer name, City,cities,PLAN TYPE, Payment mode and their Income Sources for the customers who are present in both tables.

+   2. Write a SQL statement to prepare a list with Customer name, City,cities,PLAN TYPE, Payment mode and their Income Sources for the customers who are present in both tables and their policy status is active.

+   3. Write a SQL statement to make a list with customer name, Deposit amount and their cities for those orders which deposit amount between 7000 and 10000

+   4. List of customer who are not there in secondary table but not in the primary table (hint: using right join on Email address)