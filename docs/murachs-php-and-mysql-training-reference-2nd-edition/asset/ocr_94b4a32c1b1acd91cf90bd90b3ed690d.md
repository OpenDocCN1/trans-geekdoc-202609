+   3. Use phpMyAdmin to test these statements by cutting and pasting them into phpMyAdmin.

+   4. Write the USE statement that selects the database.

+   5. Write CREATE TABLE statements to create the following tables in the ap database:

![](bbox=[0.207, 0.18, 0.86, 0.331])

When you create these tables, be sure to use the correct data types and to identify the primary key for each table. Also, make sure to automatically generate a value for each primary key. For each column, include any UNIQUE, NOT NULL, or DEFAULT attributes you think are necessary.

+   6. Use phpMyAdmin to run the script. Then, view the structure of the database.

# Add statements to the script to create some indexes and a user

+   7. Add CREATE INDEX statements to the end of the script to create indexes for the foreign keys of the invoices and lineItems tables. Also, write a CREATE INDEX statement to create an index for the invoiceNumber column.

+   8. Add a GRANT statement to the end of the script that creates a user named ap_user with a password of “sesame” and grants this user privileges to select, insert, or update data from any table in the database. However, don’t allow this user to delete any data from the database.

+   9. Test the entire ap.sql script to make sure it runs correctly.