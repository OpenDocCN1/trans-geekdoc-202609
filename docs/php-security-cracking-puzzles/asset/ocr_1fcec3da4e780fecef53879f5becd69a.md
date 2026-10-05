# Chapter II.4: MySQL and SQL Injections 201

Listing II.4.16. Escaping quotation marks

```
<table>
<form method=post>
<tr><td>Name=</</td><td><input type=text name=name value="<?php
$_POST['name'] ?>"></td></tr>
<tr><td>&nbsp;</td><td><input type=submit value='Search'></td></tr>
</form>
</table>
```php
<?php
if(!empty(\$_POST)) {
    // Connecting to the database
    require_once("config.php");

    // If the magic-quotes mode is not enabled,
    // processing the \$_POST['name'] field
    // using the mysql_escape_string() function
    if(!get_mysql_quotes_gpc()) {
        \$_POST['name'] = mysql_escape_string(\$_POST['name']);
    }

    // Searching for the user with the name \$_POST['name']
    \$query = "SELECT * FROM userslist
              WHERE name
              LIKE '\$_POST[name]%'
              ORDER BY name";
    \$usr = mysql_query(\$query);
    if(!\$usr) exit(".mysql_error()");
    while(\$user = mysql_fetch_array(\$usr)) {
        echo "The user name is - \$user[name]<br";
    }
}
?>
```
```

Because of the script, the injection query is perceived as a regular string containing part of the name. Therefore, no records will be displayed (Fig. II.4.10).