# PHP Pagination

When we display large amount of c ontent on the same page then we start thinking about adding pagination because loading all data on the same page is not the right choice in terms of optimization. So we split all our content to several pages. And in this case – each page contain some part of our information. And we can just use user -side as well as client side pagination using javascript and PHP to manage with our pages.

It’s always possible that your SQL SELECT statement query may result into thousand of records. But it is not good idea to display all the results on one page. So we can divide this result into many pages as per requirement.

Paging means showing your query result in multiple pages instead of just put them all in one page.

# A simple example to fetch records using LIMIT to ge nerate paging

```
<?php

include 'dbconnectivity.php';

// to check if page url already contain page number like
test.php?pageNum=2

if (isset($_GET['pageNum']))

{

$pageNum = $_GET['pageNum'];

} else
```