# # Chapter II.1 : Strings

![](bbox=[0.039, 0.137, 0.876, 0.303])

# ## II.1.1. Listing Files in a Directory

PHP provides a special type of quotation mark called a backtick (```). If a system command is enclosed in backticks, PHP attempts to execute it as a shell command. In the program shown in Listing II.1.1, the `dir` built-in Windows command is executed because it is enclosed in backticks.

> The `dir` command can accept both fully-qualified and relative paths to the directory as a parameter. If the parameter is not specified, the command outputs the contents of the current directory.

Listing II.1.1. Using the backtick operator to execute the dir command

```
```php
<?php
echo "<pre>";
echo convert_cyr_string(htmlspecialchars(`dir`')
```