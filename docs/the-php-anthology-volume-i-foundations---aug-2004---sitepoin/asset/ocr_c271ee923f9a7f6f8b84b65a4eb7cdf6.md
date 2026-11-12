# Keep All Configuration Central

For most PHP applications, it will be necessary to provide information describing the environment in which the script will run, including database user names and passwords, directory locations, and so on. As a general rule, try to keep the majority of this information in a single place—maybe even a single file—so that when the information needs to be modified, you can do it all in the one place. That said, when building modular applications, you may want to store elements of the configuration that are local to a specific “module” with the module itself, rather than centrally.

How exactly you choose to store this information is a matter of personal choice. In some cases, it may be worth considering an XML file or storing some of the information in a database. It’s also worth being aware of the `parse_ini_file` function, which I’ll explore in Chapter 4.

A simple but effective mechanism is to place all the settings in a single file as PHP constants, which makes them available from any function or class in your application. For example:

```
<?php
// Configuration settings
define('DOMAIN', 'sitepoint.com');

// In another script
echo 'The domain is ' . DOMAIN;
?>
```

Constants need to be used with caution, though. To make your functions and classes reusable in other applications, they shouldn’t depend on constants of a fixed name; rather, they should accept configuration information as arguments. In such cases, it’s best to use PHP variables in your central configuration file, which you can then pass to functions and classes as required. If you look at Chapter 3, when connecting to MySQL we can identify a number of variables we need to have in a central location: the server host name, the user name, the password, and the name of the selected database.

Using the require_once command we looked at in the previous solution, we can create a file called, for instance, config.php, and place it outside the public Web directories. This helps ensure that no one accidentally browses to the file containing this critical information, which would place the site’s security at risk.