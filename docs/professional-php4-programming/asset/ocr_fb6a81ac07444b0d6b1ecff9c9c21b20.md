# Action Attribute

The Action attribute tells the server which page (or script) will receive the data from the form. For example, there are two ways to call the file in which the form is defined when the user submits the form. First, by putting the file name input.php as the value of the action attribute, or second, by echo(ing) the value of $PHP_SELF in the action attribute.

$PHP_SELF is a built-in variable which always holds the name (and path if needed) of the page that is being shown. So the line:

```
<form action="?php echo($PHP_SELF) ?>\" method="POST">
```

appears as:

```
<form action="/ProPHP4/Chapter07/input.php" method="POST">
```

to the web browser. Of course, this will be seen only when we view the source of the HTML page. Using $PHP_SELF ensures ease of maintainability as the code doesn't change when the location of the file does.

# Method Attribute

This attribute determines the way information from the form is sent to the server. The two most commonly used methods are GET and POST. There are several other rarely used methods.

The GET method places the user's information into the URL. The browser simply adds a question mark at the end of URL being called by the action of the form and appends the information as name/value pairs. This addendum to the URL is known as the query string.

Additional name/value pairs are included by appending them after a "&". Try this URL: http://localhost/ProPHP4/Chapter07/input.php?you_wrote=testing+this+script&submit=Go:

![](bbox=[0.061, 0.609, 0.906, 0.79])

The input was testing this script. What happened here is known as URL encoding. Some characters cannot appear in URLs (space being one of them) and have to be converted to something acceptable (in case of space it is replaced by "+"). Thankfully, developers need not worry about how it is done because the web browser takes care of it all. Also there are several handy URL related functions in PHP to take care of encoding and decoding whenever we need to do so (see Chapter 24).