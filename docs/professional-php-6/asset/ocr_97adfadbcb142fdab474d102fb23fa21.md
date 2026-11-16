Mercifully, Smarty is sympathetic to the needs of real-world projects, for which configuration steps such as these might not always be possible (such as when your PHP scripts reside in multiple directories). You can also manually specify where these folders should exist from within your PHP code. You will learn how later in this chapter.

Next, you need to set some permissions on two of these folders: template_c and cache. Set the ownership of these folders to be that of the username of your Web server. In most cases, this is the nobody user, but it may also be apache or various others. If you are unsure, you can check by issuing the following:

```
ps auxw | grep httpd | grep -v grep | awk '{print $1}' | tail -1
```

What is important here is that this user, and the group of which that user is a member, can read and write to these folders freely. Set permissions as follows:

```
chown nobody.users ./cache
chown nobody.users ./template_c
chmod 770 ./cache
chmod 770 ./template_c
```

The mode 770 means that the owner of these folders may read, write, and execute the contents, and that no one else may. If this bothers you, and you are unable to become the root on this machine, you may want to use 775 instead, which allows others read and write access. You may, however, rightly deem this to be a security risk.

# Using Smarty

A typical Smarty implementation consists of a controller (much as before) ending in .php, and a template file representing the view, this time ending in .tpl.

# smartytest.php

Take a look at the following very simple example:

```
<?
require('Smarty.class.php');

$objSmarty = new Smarty;
$strTemplate = "smartytest.tpl";

$objSmarty->assign("test_variable", "This is the value of my test variable");

$objSmarty->display($strTemplate);
?>
```

You must also enter the template code for this script, which must reside in the folder called template that you have created underneath this one.