```
```php
$sql = 'SELECT COUNT(*) AS matched FROM users WHERE username='
. $username . "' AND password='" . $password . "'";
$result = mysql_query($sql);
.
$array = mysql_fetch_array($result);
$windows['main']->disconnect($disconnect_id);
$windows['main']->destroy();
.
if ($array['matched'])
    loadSearchPage();
else
    quit("Authentication failed\n");
}
```
```

Our final two functions, quit() and destroyWnd(), are both used to exit the program. quit() accepts one argument which it then prints to the command line before exiting the program, and destroyWnd() is used as a callback by both our login and search windows so that if the user clicks the X in the window decoration they will exit the program accordingly:

```
```php
function quit($msg)
{
    printf($msg . "\n");
    gtk::main_quit();
}
.
function destroyWnd()
{
    gtk::main_quit();
}
}
```
```

The final few lines of code load the PHP-GTK extension as was described with the "Hello World" example. We then call the loadMainWindow() function to show the login page and finally, as with all PHP-GTK applications, we call gtk::main() to start running PHP-GTK's main loop:

```
```php
if (strtoupper(substr(PHP_OS, 0, 3)) == 'WIN')
    dl('php_gtk.dll');
else
    dl('php_gtk.so');
.
loadMainWindow();
gtk::main();
?>
```
```

A little exercise for the reader might be to alter the quit() function so that rather than outputting error messages to the command line it pops up a little dialog box telling the user about the error (hint: take a look at GtkDialog).