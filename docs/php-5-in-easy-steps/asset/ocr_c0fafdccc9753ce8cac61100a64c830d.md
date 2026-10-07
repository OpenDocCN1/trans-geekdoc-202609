# ...cont'd

```
#select the database
$rs = @mysql_select_db ("my_database", $conn )
or die ( "Could not select database" );
```

![](bbox=[0.133, 0.083, 0.283, 0.213])

```
#create the SQL query
if ($name and $comments ) {
  $sql = "insert into guestbook (name, email, comments)\nvalues (\$name\,\\$email\,\\$comments\");
  $rs = @mysql_query($sql, $conn )
or die ( "Could not execute SQL query" );
```

```
#confirm entry and display a link to guestbook
if ($rs) {
  $msg = "<h3>Thank you - your entry has been saved.";
  $msg = "<br><a href=\"guestbook-view.php\";
  $msg = "View My Guestbook</a>/h3";
}
```

```
#write the page
echo ($ msg );
?>
</body></html>
```

This illustration shows the form redisplayed after submission of an incomplete form
- there is no entry in the comments field. Notice that the previous entries are retained by assigning their PHP variable values to the form's HTML value attributes. A successful submission is illustrated on the next page.

![](bbox=[0.023, 0.627, 0.127, 0.707])

| Sign the guestbook |
|---||
| Address | http://localhost/guestbook-sign.php | Go |
| Name | Tony |
| Email | tony@abc.com |
| Comments: |

13. A PHP guestbook | 169