# Chapter 13: Retrieving Data from MySQL with PHP

```
?php if ($start + PAGE_SIZE < $totalRows ) ?>
<a href="view_members.php?start=<?php echo min($start + PAGE_SIZE, $totalRows) ?>&amp;order=<?php echo $order ?>">Next page</a></p>
<?php } ?>
</div>
```

```
?php
displayPageFooter();
?>
```

This script uses the Member class to retrieve the list of members from the database, then displays the list. It starts by retrieving two query string parameters — start, representing the record position from which to start displaying records in the page, and order, which specifies which column to sort the data — and storing the parameter values in two variables, $start and $order. If either parameter not passed a default is used. To improve security, the script filters both parameters to make sure they contain valid values: $start is cast to int, whereas $order uses a regular expression to remove any non-alphabetic characters (because only letters are used for the field names in the members table).

You can find out more about regular expressions in Chapter 18.

Next, the script retrieves the list of members to display in the page. The code is to really simple, because all the complexity is hidden inside the Member class:

```
list($members, $totalRows) = Member::getMembers($start, PAGE_SIZE, $order);
```

Member::getMembers() is called, passing the number to start retrieving records from, the number of records to retrieve, and the string to use for the ORDER clause. getMembers returns a two-element array. The first element — the list of Member objects — is stored in $members, and second element — the total number of members in the members table — is stored in $totalRows.

Now that the data is retrieved, if simply a case of displaying the list in the page, displayPageHeader() is called with an appropriate title to give the HTML header. The XHTML element table is generated, with three header cells for first, name, and last name:

```
?php if ($order == "username") ?><th><a href="view_members.php?order=<?php echo $username ?>">Username</a><?php if ($order == "username") ?>?<?php else; ?>?/</th>
<?php if ($order == "firstName") ?><th><a href="view_members.php?order=<?php echo $firstName ?>">First Name</a><?php if ($order == "firstName") ?>?<?php else; ?>?/</th>
<?php if ($order == "lastName") ?><th><a href="view_members.php?order=<?php echo $lastName ?>">Last Name</a><?php if ($order == "lastName") ?>?<?php else; ?>?/</th>
```

In each case, the column name is linked to a URL, with run_members.php again to sort by that column. However, if the data is already sorted by a particular column, that column's name isn't linked, in to indicate that the data is sorted by column.

397