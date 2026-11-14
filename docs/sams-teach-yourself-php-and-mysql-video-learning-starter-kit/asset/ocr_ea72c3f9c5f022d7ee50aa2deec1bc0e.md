```
<?php
echo "Hello Web!";
?>
```

```
<%
echo "Hello Web!";
%>
```

```
<script language="php">
echo "Hello Web!";
</script>
```

You can also put single lines of code in PHP on the same line as the PHP start and end tags:

```
<? echo "Hello Web!"; ?> .
```

Now that you know how to define a block of PHP code, let’s take a closer look at the code in Listing 4.1 itself.

# The echo Statement and print() Function

Simply put, you use the echo statement to output data. In most cases, anything output by echo ends up viewable in the browser. Alternatively, you could have used the print() function in place of the echo statement. Using echo or print() is a matter of taste; when you look at other people’s scripts, you might see either used.

Whereas echo is a statement, print() is a function. A function is a command that performs an action, usually modified in some way by data provided for it. Data sent to a function is almost always placed in parentheses after the function name. In this case, you could have sent the print() function a collection of characters, or a string. Strings must always be enclosed in quotation marks, either single or double, as in this example:

```
<?
print("Hello Web!");
?>
```

The only line of code in Listing 4.1 ended with a semicolon. The semicolon informs the PHP engine that you have completed a statement.