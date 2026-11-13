Error reporting can be forced off by disabling the `display_errors` directive in the `php.ini` file. This ensures error reporting can't accidentally be turned back on.

When accessed through the browser, this code would allow all errors to be visible, display vital server information, force a failed attempt to the database exposing the true path of file, as you can see in Figure 7.1, and determine if a database exists.

# Using a better way to check for file extensions

Going back to the simple upload example, let's add more robust security measures. The major change to the code is the if statement that checks for a valid file extension. Instead of looking for the existence of a file type, it looks at the end of the filename and retrieves the actual correct extension.

```
if(strrpos( $file['name'], '.jpg') != false)
{
    ...
}
```

# FIGURE 7.1

Error message returned when database is intentionally set to fail on connection

![](bbox=[0.115, 0.49, 0.755, 0.875])