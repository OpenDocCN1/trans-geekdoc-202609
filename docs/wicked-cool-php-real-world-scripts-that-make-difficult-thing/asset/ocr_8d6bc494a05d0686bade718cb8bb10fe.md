variable. To show you how it works, we'll assume that our basic.tpl file looks like this:

```
<HTML>
<head>
<title>{$assigned_title}</title>
</head>
<body>
My name is {$assigned_name}.
</body>
</HTML>
```

There are two variables here, $assigned_title and $assigned_name. To set the variables so that Smarty displays those values, use the assign() method, as follows:

```
<?php

require_once("smarty_initialize.php");

$page_title = "The Smarty Template Test";
$page_name = "William Steinmetz";

$smarty->assign("assigned_title", $page_title);
$smarty->assign("assigned_name", $page_name);

$smarty->display("basic.tpl");

?>
```

You can assign the variable to just about any kind of PHP string data; it doesn't matter if it's MySQL data, HTML from some other source, user-supplied data, or what have you. If everything goes smoothly, the HTML renders as shown in Figure 1-1.

![](bbox=[0.241, 0.629, 0.725, 0.781])

Figure 1-1: HTML displayed in a browser

# What Can Go Wrong?

Aside from typical mundane incorrect path errors, the most common error that you'll encounter is that the webserver cannot write to the compile directory you've defined for the compiled Smarty templates. If the