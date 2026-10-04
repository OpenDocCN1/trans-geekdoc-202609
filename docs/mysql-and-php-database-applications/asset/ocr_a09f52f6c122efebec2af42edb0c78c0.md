# Chapter 11: Content Management System

```
$mylink = @mysql_connect("localhost", $PHP_AUTH_USER, $PHP_AUTH_PW)
or or authenticate
($realm,"Could not login to db as $PHP_AUTH_USER")
```

```
mysql_select_db("nethoth");
```

As you look at the preceding code, keep in mind that in this script people the application need to be able to change the usernames and passwords that they are using to log into the application—i.e. log in a different user. If you go through the script by step, you should know how to do it. We'll go through it line-by-line after one quick explanation.

Within the index.php page, there is a submit button that, when pressed, will that the user wants to login under a different username and password. The following creates the form with the submit button.

```
print paragraph("php")
  start_form("index.php")
    hidden_field("olduser",$PHP_AUTH_USER)
    submit_field("newuser","Log As New User")
  end_form("");
```

Using the functions described in chapter 9, this code creates a form, if submitted, sends the variables $olduser and $newuser back to the index.php page. When the form is submitted and the variables are sent, they will hit this portion of the authenticate.php page.

```
if (empty($PHP_AUTH_USER))
|| || (!empty($newuser) && $newuser == $PHP_AUTH_USER ))
```

The preceding block will test true under two conditions. If the first, the user has not yet logged in, because in case $PHP_AUTH_USER will be empty. The other condition comes from the form we just discussed. If submit button is pressed, $newuser will not be empty and Solduser will contain the value of $PHP_AUTH_USER, meaning the user wants to change their login name and password. If either of these is true, the following code will run:

```
$what = empty($PHP_AUTH_USER) ? "login" :
  "newuser($newuser,$olduser)"
  authenticate($realm,$errmsg.":$what");
```