```
printf("<tr><td>%s</td><td>%s</td></tr>",
               $name, implode(" ", $value));
        } else {
            printf("<tr><td>%s</td><td>%s</td></tr>",
                   $name, $value);
        }
    }
?>

```

```
</table>
<h1>Environment variables</h1>
<table><tr><th>Name</th><th>Value</th></tr>
```

```
<?php
ksort($_ENV);
foreach ($_ENV as $name => $value) {
    if (is_array($value)) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
               $name, implode(" ", $value));
    } else {
        printf("<tr><td>%s</td><td>%s</td></tr>",
               $name, $value);
    }
}
?>

```

```
</table>
```

# Listing 8.21 Output of All Environment Variables ("environmentvariables.php")

The consequence of the system differences is clear: If you query an exotic environment variable (as a rule of thumb, one that does not begin with `HTTP_` or `PHP_`), then you should also test the code on other operating systems. Otherwise, you may be faced with unpleasant surprises if you move the server. But there are also differences in the more familiar environment variables; for example, the `HTTP_UA_CPU` and `HTTP_UA_OS` environment variables are specialties of Internet Explorer and therefore only suitable for intranet use.

The only question that remains is what the difference is between `$_SERVER` and `$_ENV`. In theory, `$_SERVER` contains variables that have to do with the HTTP request and response, whereas `$_ENV` contains environment variables of the system on which PHP is running. In practice, however, this is only ever the case with Linux; with Windows, the two are often mixed up (as we have seen). Depending on the configuration in the `php.ini`, it can also be that some of the superglobals are not accessible, p.e. `$_ENV` is not recommended in production environments. As a hint, typically use `$_SERVER`.