6. Open and run any of the other examples in this chapter that you're interested in reviewing.

# Write your own SELECT statements

7. Use phpMyAdmin to write and test a SELECT statement that selects the productName, description, and listPrice columns for all rows in the products table.

Add code to this statement so it sorts the result set by list price. Then, run this statement again to make sure it works correctly. This is a good way to build and test a statement, one clause at a time.

Add code to this statement so it only selects rows that have the word “electric” in the description column, and run this statement again to make sure it works correctly. Then, save this statement in a file named select_products.sql in the ex_starts/ch18_ex1 directory.

8. Write a SELECT statement that joins data from the customers and addresses tables. This statement should select these columns: firstName, lastName, line1, line2, city, state, zipCode. It should only select the billing addresses for customers who have a last name of “sherwood”. Then, save this statement in a file named select_billing_addresses.sql in the ex_starts/ch18_ex1 directory.

9. Write a SELECT statement that returns a count of the number of products in the category that has a name of “Guitars”. To do this, use a subquery to get the category ID. Then, save this statement in a file named count_products_by_category.sql in the ex_starts/ch18_ex1 directory.

# Write your own INSERT, UPDATE, and DELETE statements

10. Write an INSERT statement that adds a customer named John Smith to the customers table. Use an email address of “johnsmith@example.com” and a password of “sesame”. Then, save this statement in a file named insert_customer.sql in the ex_starts/ch18_ex1 directory.

11. Write an UPDATE statement that changes the password for John Smith to “5e5ame!”. Then, save this statement in a file named update_customer.sql in the ex_starts/ch18_ex1 directory.

12. Write a DELETE statement that deletes the customer named John Smith. Then, save this statement in a file named delete_customer.sql in the ex_starts/ch18_ex1 directory.

13. To restore the database to the way it was initially, run the creation script again as you did in step 3.