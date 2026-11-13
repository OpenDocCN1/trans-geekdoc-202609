```
if (empty($errmsg))
{
    $query = <<<EOQ
insert into guestbook (name,location,email,url,comments,remote_addr)
values ('%s','%s','%s','%s','%s','%s')
EOQ;
    $query = sprintf($query
    , mysql_real_escape_string($name)
    , mysql_real_escape_string($location)
    , mysql_real_escape_string($email)
    , mysql_real_escape_string($url)
    , mysql_real_escape_string($comments)
    , mysql_real_escape_string($_SERVER['REMOTE_ADDR'])
    );
    safe_mysql_query($query);
    print "<h2>Thanks, $name!!</h2>\n";
}
else
{
    print <<<EOQ
<p>
<font color=red>
<b>
<ul>
$errmsg
</li>
Please try again
</font>
</p>
EOQ;
    return $errmsg;
}
```

This function is going to make sure that the information entered is moderately useful. If there is a problem with the information, a text string describing the problem will be assigned to the variable $errmsg. If, after the function is executed, $errmsg is empty, the values will be inserted into the database. Otherwise the error message(s) will be printed, and the values the user entered will be assigned to globals so that they can be printed as the default values in the text fields the next time through.