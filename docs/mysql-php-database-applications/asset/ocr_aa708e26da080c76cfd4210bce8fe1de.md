This is it. You use the global $offset variable to run the query with the select_entries() function, and then print the results by calling the print_entry() function within a while loop. Navigational elements are determined by the nav() function.

# DELETING ENTRIES

The most complex portion of this application involves the ability to delete entries from the guestbook. This stands to reason because you don't want your guestbook being fooled with by anonymous users. So the first thing you need to do before deleting an entry is authenticate users. When discussing the guestbook_authenticate() function, we showed how an HTTP 401 header will bring up the browser's username-and-password dialog box. The values entered need to be checked against the guestbook_admin database table. The guestbook_authenticate() function takes care of this for you, which is why it's called at the top of the edit.php file.

```
<?php

ob_start();

require_once('header.php');
guestbook_authenticate();

ob_end_flush();

guestbook_start_page('Edit The Guest Book');

?>
```

We use the PHP output buffering functions, ob_start() and ob_end_flush(), to make sure that no output gets sent to the browser before the HTTP 401 header. Otherwise, a blank line or space outside the <?php ... ?> tags in the header.php would prevent guestbook_authenticate() from running. If you know you won't be using PHP as an Apache module, then you know PHP won't be trying to send these headers, and you can remove this code. It shouldn't make any visible difference if you leave it in, however.

Once a valid username and password have been entered, the remainder of the edit.php file will be sent. But this time, in addition to all the other information, a checkbox will be included so the user can decide which entries should be deleted. The value of the checkbox will be the primary key of the guestbook table.

```
while ($row = mysql_fetch_array($result))
{
    // call the normal function to display a guestbook entry
    print_entry($row,$preserve,'name','entry date','location','email'
    ,'URL','comments'
```