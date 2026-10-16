We can assume the SQL query to produce this output might be structured like this:

```
SELECT <some fields> FROM <a table> WHERE <search field> LIKE '%<search term>%';
```

Since this is a LIKE query, the % are wildcards. If we search the inventory for anything with sir in it, we get output in Figure 22.5.

To detect if the application is directly inserting data from entered form fields into an SQL query, we can insert a single quote (') to create a malformed SQL query like in Figure 22.6.

This output is faulty and indicates our application is vulnerable to SQL injection. It's even worse because we can manipulate the application into returning information in the database. Let me show you how.

![](bbox=[0.48, 0.18, 0.86, 0.44])

> > **Do not** perform any of what I am about to show you on any website unless you are explicitly contracted and qualified to perform penetration testing for said website!

![](bbox=[0.48, 0.48, 0.86, 0.62])

We need to understand that the only part of the query we can control is what is entered in between the two percent signs (%). We can imagine that our PHP code that performs the query might look something like this:

```
$search_term = isset($_POST['search']) ? $_POST['search'] : '';

$query = "SELECT some_field_1, some_field_2, some_field_3 FROM SomeTable "
    . "WHERE some_field_n LIKE '%$search_term%'";
```

I can now manipulate the query to return almost anything I want. I can test that by entering the following into the search field:

```
' ;--
```