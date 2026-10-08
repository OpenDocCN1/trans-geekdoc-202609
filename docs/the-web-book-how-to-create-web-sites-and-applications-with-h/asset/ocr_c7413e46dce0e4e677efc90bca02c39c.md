# # Accessing MySQL Databases with PHP

On page 190 we covered the basics of creating a web-based MySQL database and querying it via phpMyAdmin. On page 208 we covered writing programs using PHP. And on page 239 we covered HTML forms. Once you know how to do these three things (and if you have forgotten, you would be advised to recap before going further), we can now put it all together and create an online database application.

To continue, you will need to ensure that the hms database we discussed on page 187 exists on the web server, and that there's a table within it called customers. The customers table needs 7 fields:

+   - id
- firstname
- surname
- title
- address
- phone
- email

All of these should be text fields (tinytext should suffice) except id, which should be an integer. Further, id should be set as an auto-increment field. If you've forgotten how to do so, refer back to page 190 for coverage of phpMyAdmin.

With the database and table created, your phpMyAdmin screen should look like this when you view the structure of the Customers table: