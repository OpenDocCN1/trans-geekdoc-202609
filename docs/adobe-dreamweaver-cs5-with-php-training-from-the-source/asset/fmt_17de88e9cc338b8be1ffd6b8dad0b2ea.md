
lesson11/start/list_places.php
lesson11/start/update_photo.php
lesson11/start/update_place.php
***Completed Files***
lesson11/completed/delete_photo.php
lesson11/completed/delete_place.php
lesson11/completed/list_photos.php
lesson11/completed/list_places_01.php
lesson11/completed/list_places_02.php
lesson11/completed/update_photo.php
lesson11/completed/update_place_01.php
lesson11/completed/update_place_02.php
lesson11/completed/scripts/db_definitions_04.php
lesson11/completed/scripts/db_definitions_05.php
lesson11/completed/scripts/db_definitions_06.php
lesson11/completed/scripts/db_definitions_07.php
lesson11/completed/scripts/db_delete_place_01.php
lesson11/completed/scripts/db_delete_place_02.php
lesson11/completed/scripts/db_update_photo_01.php
lesson11/completed/scripts/db_update_photo_02.php
lesson11/completed/scripts/db_update_place_01.php
lesson11/completed/scripts/db_update_place_02.php
lesson11/completed/scripts/library.php
In this lesson, you’ll complete the multiple-table CMS from [Lesson 10](#ch10.html#ch10). To update records, you need to select the data stored in related tables and display it in a form ready for editing. When the form is submitted, the data must be validated again before the database can be updated. Fortunately, you can reuse many of the functions defined for the insert forms in the previous lesson. You’ll also use `Zend_Paginator` to display database results over several pages.

*The photo management page draws data from the file system and three separate tables.*

![image](graphics/fig11_01.jpg)

### Selecting Records with SQL

Now that you have records stored in multiple tables, it’s necessary to take a more detailed look at how to select records. The basic syntax of a `SELECT` query looks like this:

SELECT column(s)  

FROM table(s)  

WHERE condition  

ORDER BY column(s)

SQL keywords are case insensitive, but the normal convention is to type them in uppercase to make them easier to identify. Splitting the query over several lines is also only a convention, but it enhances readability and maintenance.

The `WHERE` and `ORDER BY` clauses are optional. In fact, there are several other options that have been omitted here for the sake of simplicity.

#### Selecting all records in a table

To retrieve all records in the `places` table, the `SELECT` query looks like this:

SELECT \* FROM places

This selects every record in every column of the `places` table. Unless you really need every column, it’s better to specify the columns you want by listing them separated by commas. For example,

SELECT place_id, name, description  

FROM places

This selects the named columns from all records in the `places` table.

#### Specifying search criteria with WHERE

Adding a `WHERE` clause narrows down the results, usually by specifying a value to match or a comparison. For example,

SELECT place_id, name, description  

FROM places  

WHERE name = 'San Francisco’

This retrieves the `place_id`, `name`, and `description` fields for the record that has San Francisco as the value in the `name` column.

### ![image](graphics/note.jpg)**NOTE:**

Unlike PHP, SQL uses a single equals sign to test for equality.

You can specify multiple conditions in a `WHERE` clause by separating the conditions with the keywords `AND` and `OR`. For example,

SELECT place_id, name, description  

FROM places  

WHERE name = 'San Francisco’ OR created >= '2010-01-01'

This retrieves San Francisco *and* all records created since January 1, 2010. If you use `AND`, it finds San Francisco only if the record was created on that date or later.

#### Specifying the sort order

By default, a `SELECT` query returns the results in the same order as they are stored in the database. Initially, this is the same order as the data was inserted but is likely to change as records are updated or deleted. To specify the order of results, add an `ORDER BY` clause, listing the column(s) that determine the order. You can specify a column, even if it’s not included in the `SELECT` part of the query. For several columns to affect the order, add them as a comma-separated list in order of precedence like this:

SELECT place_id, name, description  

FROM places  

ORDER BY created, name

This retrieves the three named columns with the results sorted chronologically by their date of creation. Any records that were created at the same time are sorted alphabetically by the `name` column.

### ![image](graphics/note.jpg)**NOTE:**

In this example, the `name` column has no effect, because the `created` column stores both date and time. In [Lesson 12](#ch12.html#ch12) you’ll see how to extract date parts from a `DATE` or `TIMESTAMP` column.

By default, the sort order is ascending—in other words, alphabetical, smallest to largest, or oldest to most recent. To sort in reverse (descending) order, add the keyword `DESC` after the column name like this:

SELECT place_id, name, description  

FROM places  

ORDER BY created DESC, name

This sorts the results with the newest record first.

You can use `ORDER BY` without specifying a `WHERE` clause. However, if you include a `WHERE` clause, it must come *before* `ORDER BY` like this:

SELECT place_id, name, description  

FROM places  

WHERE created >= '2010-01-01’  

ORDER BY created DESC

If you put the `WHERE` clause *after* `ORDER BY`, the database rejects the query.

#### Joining tables

When data is stored in separate tables, you retrieve related data by joining the tables on the fly. You list the names of the columns after the `SELECT` keyword and perform the join(s) in the `FROM` clause. Where columns share a common name, you must prefix the column name with the table name separated by a period. For example, you distinguish between the `state_id` columns as `states.state_id` and `places.state_id`.

The most common type of join is an `INNER JOIN`. Used on its own, it produces what’s known as a *Cartesian join*—every possible combination of rows from both tables. This is rarely practical, so you normally qualify the join by adding a condition, such as matching the foreign key of one table to the primary key of the other table using an `ON` clause. This is how you join the `places` and `states` tables to get the state name associated with each place:

SELECT name, state_name  

FROM places  

INNER JOIN states ON places.state_id = states.state_id

The result looks like this:

![image](graphics/fig11_02.jpg)

The values stored in `places.state_id` are the USPS abbreviations for the states, but using `INNER JOIN` to match `states.state_id` allows you to retrieve the value of `state_name` for each record in the `places` table.

An alternative syntax is to use `WHERE` instead of `ON`:

SELECT name, state_name  

FROM places   

INNER JOIN states WHERE places.state_id = states.state_id

Although a `WHERE` clause can be used to specify the condition for joining tables, it’s recommended to use `ON`. Use `WHERE` to restrict which rows you want in the result set.

### ![image](graphics/note.jpg)**NOTE:**

MySQL also permits you to replace `INNER JOIN` by a comma when using `WHERE` to specify the condition. However, this syntax sometimes causes errors and is not recommended in MySQL 5.0 or later.

When the same name is used in both tables, you can use this syntax:

SELECT name, state_name  

FROM places   

INNER JOIN states USING (state_id)

#### Using a LEFT JOIN to find missing values

Let’s say that California has been accidentally deleted from the `states` table. Using `INNER JOIN` on the same data produces this result:

![image](graphics/fig11_03.jpg)

`INNER JOIN` works only when there are matching rows in both tables. To find all places, even if there isn’t a matching value in the `states` table, use a `LEFT JOIN`. The syntax is the same:

SELECT name, state_name  

FROM places  

LEFT JOIN states USING (state_id)
