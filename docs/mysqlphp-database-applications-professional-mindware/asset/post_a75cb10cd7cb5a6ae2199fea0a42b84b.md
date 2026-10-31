
```
<table border=0>

<?php

if (empty($offset)) { $offset = 0; }

$result = select_entries($offset);
$preserve = "";
while ($row = mysql_fetch_array($result))
{
    print_entry($row,$preserve,"name","location","email","URL","entry date","comments");
    print "<tr><td colspan=2>&nbsp;</td></tr>\n";
}
mysql_free_result($result);
?>

</table>
<?php
nav($offset);

include "end_page.php";
?>
```

This is it. You determine a value for $offset, run the query with the select_entries() function, and then print the results by running the print_entry() function within a while loop. Navigational elements are determined by the nav() function.

## DELETING ENTRIES

The most complex portion of this application involves deleting entries from the guestbook. This stands to reason because you don't want your guestbook being fooled by anonymous users. So the first thing you need to do before deleting an entry is authenticate users. When discussing the authenticate() function, we showed how an HTTP 401 header will bring up the browser's username and password dialog box. The values entered then need to be checked against the guestbook_admin database table. The authenticate.php file takes care of this for you, which is why this file is included in the edit.php file.

The heart of authenticate.php is this:

```
if (empty($PHP_AUTH_USER))
{
    authenticate($realm,$errmsg,"header");
}
```
```
else
{
    $query = "select username from guestbook_admin where password = password(lower('$PHP_AUTH_PW')) and username = lower('$PHP_AUTH_USER')";
    $result = mysql_query($query);
    if ($result) { list($valid_user) = mysql_fetch_row($result); }
    if (!$result || empty($valid_user))
    {
        authenticate($realm,$errmsg,"query");
    }
}
print "<p><b>Editing as $PHP_AUTH_USER</b></p>\n";
```

If no username has been entered the header is sent through your authenticate() function. If the username does exist, a query is sent to the database to validate the user. If a row is returned, the user is validated and can continue working; otherwise the header is sent again.

Once a valid username and password have been entered, the remainder of the edit.php file will be sent. But this time, in addition to all the other information, the checkbox will be included, so the user can decide which entries should be deleted. The value of the checkbox will be the primary key of the guestbook table.

```
while ($row = mysql_fetch_array($result))
{
    print_entry($row,$preserve,"name","entry
date","location","email","URL","comments");

    print " <tr>\n";
    print "  <td valign=top align=right><b>Delete?</b></td>\n";
    print "  <td valign=top align=left><input type=checkbox
name=\"entry_id[]\" value=\"" . $row["entry_id"] . "\"> Yes, delete
entry #" . $row["entry_id"] . "</td>\n";
    print " </tr>\n\n";

    print "<tr><td colspan=2>&nbsp;</td></tr>\n";
}
```

This form is then submitted to the confirm_delete.php file. Notice how you're passing an array here. The name of the form element is entry_id[], which means that when this form is passed to PHP, entry_id will become an array. The number of values in the array depends on the number of boxes checked. HTTP will not send the unchecked boxes at all.

The first time through the confirm_delete.php file, we will print out the entries. This will make the person deleting these entries make sure he or she isn't doing something stupid.

```
while (list($key,$value) = each($entry_id))
{
    print "<li>Delete entry #$value?\n";
    print "<input type=hidden name=\"entry_id[]\" 
value=\"$value\">\n";
}
```

If any of these entries are to be deleted, this page will submit to itself, with a different value (Confirm Delete) sent with the submit button. This will make the following code run:

```
while (list($key,$value) = each($entry_id))
{
    print "<li>Deleting entry #$value\n";
    $q = "delete from guestbook where entry_id = $value";
    safe_query($q);
}
```

We loop through the $entry_id array, deleting records for each member.

## Scripts

There are a few more scripts, but these don't warrant much discussion. sign.php, start_page.php, end_page.php, and confirm_delete.php, are included on the CD. We suggest you look at them and the comments to get a feel for how they fit into the application.

## Summary

The skills you learned here may not get you the big bucks as a programmer, but if you understand everything that is being done here, you should be in pretty good shape as you move forward in your PHP programming life.

In particular, you should see the priority that is put on creating reusable code. Nearly everything we have is in functions. This makes it much more likely that the code we write will be usable in some future application.

Additionally, you got to see some basic validation. Validation is an important concept and one you will need to take very seriously when your application allows for user input. If you'd like to see how seriously some people take validation, check out Manual Lemos' form validation class, which is included on the CD.

## Chapter 9
### Survey
### IN THIS CHAPTER
- Learning functions for creating HTML tags
- Understanding data that use a relational structure
- Putting MySQL's date functions to work

IF A GUESTBOOK IS the most common application on the Web, a survey isn't far behind. Many sites have some sort of widget that lets you choose you favorite color or sports hero, or whatever, to see what percentage of voters take what stance. So let's go forth and create a survey.

In this application there will be a bit more complexity than you saw in Chapter 8. The programming will get a bit trickier, and the administration of the application will require more work. Unlike the guestbook, this application will require some knowledge of database theory. There are related tables, complete with the primary and foreign keys discussed in Section 1 of this book. This means that your SQL queries will include joins.

### Determining the Scope and Goals of the Application

A survey application could be ultra-simple. If you wanted only to gather responses from a single question and return basic statistical information on the responses (how many votes for choice A, B, and so on), you wouldn't need a whole lot of code (or a chapter explaining it). A single table that stored answers would do the trick. The question could even be hard-coded into the HTML. But that would not make for very interesting learning experience, would it?

It gets more interesting if there can be any number of questions. Instead of just one, this application will allow for two, five, ten, or more — whatever you want. Not only that, this survey will record demographic information (such as age and country of origin) and allow for sorting on the basis of this information. We also decided to add the ability to pick a winner from those who filled out the personal information — this might encourage people to give real rather than fictitious answers.

There is one more wrinkle to discuss here. There is really no way to create a survey application that records perfect data. Even if you go to extreme lengths, there will always be an opportunity for the shrewd and persistent to submit multiple entries. But in all likelihood your survey will not have to pass muster with the Federal Elections Commission. A small step to weed out those ruining your survey should do the trick, and you will see one way to accomplish this later on.

### Necessary Pages

Entering and viewing information will require three pages. The first is where the questions will be presented and where the user will enter name, address, and geographic and demographic information. A second page will show the basic survey results. A third will give a detailed breakdown. Figures 9-1, 9-2, and 9-3 show these pages respectively.

![](img/de0823012275cf4ceebdb822a56e6b71_246_0.png)

Figure 9-1: Page for filling out survey

Note that for this application you will use a .gif file for your chart. The script will change the size attributes of the gif in the <img> tag to give a representation of the information. This works, but isn't necessarily ideal. You could install the gd libraries and compile PHP with the -with-gd flag. These functions are beyond the scope of this book.

This application, like all others, needs some administrative tools. For starters, you will need to be able to add, delete, and edit questions. Additionally, there is a page that selects a winner at random from the database. Figures 9-4 and 9-5 show the administrative page and the select winner page, respectively.
