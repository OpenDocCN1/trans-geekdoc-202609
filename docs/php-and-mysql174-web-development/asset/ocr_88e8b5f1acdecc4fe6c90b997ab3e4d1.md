# Creating a Simple Session Example

Some of this discussion might seem abstract, so let's look at an example. Here, you'll implement a set of three pages.

On the first page, start a session and create the variable $_SESSION['session_var']. The code to do this is in Listing 22.1.

Listing 22.1 page1.php—Starting a Session and Creating a Session Variable

```
<?php
session_start();

$_SESSION['session_var'] = "Hello world!";necho 'The content of ' .$_SESSION['session_var'].' is ' . .$_SESSION['session_var'].'<br>';
?>
<a href="page2.php">Next page</a>
```

This script creates the variable and sets values. The output of this script is shown in Figure 22.1.

![](bbox=[0.119, 0.487, 0.613, 0.718])

Figure 22.1 Initial value of the session variable shown on the page is the one that will be available on subsequent

The final value of the variable on the page is the one that will be available on subsequent pages. At the end of the script, the session variable is serialized, or frozen, until it is reloaded the next call to session_start().

You can therefore begin the next script by calling session_start(). This script is shown in Listing 22.2.