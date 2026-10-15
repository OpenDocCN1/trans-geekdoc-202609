Let‘s create a PHP page [view.php](view.php) which should receive two variables values as follow-  
city =Gurgaon, state=Haryana

# view.php

```
```php
<?php

echo "Location is ".\$_REQUEST['city']." ".\$_REQUEST['state'];

?>
```
```

You can also retrieve everything after the ? And assign it to a variable, we can simply use \$_SERVER super global like so:

```
```php
<?php

\$txt = \$_SERVER['QUERY_STRING'];

var_dump(\$txt);

?>
```
```

Please note, if there is no query string, then the QUERY_STRING key in \$_SERVER will be an empty string