# Core PHP Programming

The pg_loreall function reads an entire large object and sends it directly to the browser.

```
<?
$File = pg_looper($Connection, $Object, "r");
pg_loreall($File);
?>
```

# pg_lounclick(integer file, integer object)

Use pg_lounlink to delete a large object.

```
<?
$Object = pg_locreate($Connection);
$File = pg_looper($Connection, $Object, "r");
pg_lounlink($File, $Object);
?>
```

# pg_lowrite(integer file, string buffer)

The pg_lowrite function writes the buffer to the large object.

```
<?
$Object = pg_locreate($Connection);
$File = pg_looper($Connection, $Object, "w");
pg_lowrite($File, "some text");
?>
```

# integer pg_numfields(integer result)

The pg_numfields function returns the number of fields in the result set. See pg_exec for an example of use.

# integer pg_numrows(integer result)

Use pg_numrows to get the number of rows in the result set. See pg_exec for an example of use.

# string pg_options(integer connection)