# PHP variables

These are variables available through PHP.

# PHP_SELF

This is the address of the file running. Usually, the full path is given from the ServerRoot directory, which is very useful when a form is both presented and processed in the same PHP page.

```
<?
if(isset($sum)) {
    //do some form processing here
    echo "thanks for the submission";
} else {
?>
<form name=myform method=post action=<?$PHP_SELF?>
  <input type=text name=first_name> first name<br>
  <input type=text name=last_name> last name<br>
  <input type=submit name=submit value=submit>
</form>
<?
}?>
```

Keep in mind that PHP_SELF always refers to the name of the script being executed in the URL. In an include file, PHP_SELF will not refer to the file that has been included. It will refer to the script being run.

It's worth noting that PHP_SELF behaves strangely when PHP is run on Windows or a CGI module. Make sure to look at phpinfo() to see the value of $_PHP_SELF on your system.

# HTTP_POST_VARS

This is the array that contains all the variables sent through the POST method, usually through forms. You can access each individual variable as an element in an associative array (for example $_PHP_POST_VARS["idname"]).

# HTTP_GET_VARS

This is the array that contains all the variables sent through the GET method. You can access each individual variable as an element in an associative array (for example $_PHP_GET_VARS["idname"]).

# HTTP_COOKIE_VARS

All of the cookies sent to the browser will be readable in this associative array. This includes the session cookie. If you are wondering how your cookies are