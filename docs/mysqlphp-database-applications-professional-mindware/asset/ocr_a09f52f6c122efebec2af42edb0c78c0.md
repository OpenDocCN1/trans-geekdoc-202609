```
$mylink = @mysql_connect("localhost", $PHP_AUTH_USER, $PHP_AUTH_PW)
    or authenticate
    ($realm,"Could not login to db as $PHP_AUTH_USER");

mysql_select_db("netsloth");
```

As you look at the preceding code, keep in mind that in this script people using the application need to be able to change the usernames and passwords that they are using to log into the application—i.e., log in as a different user. If you go through the script step by step, you should see how to do it. We'll go through it line-by-line after one quick explanation.

Within the index.php page, there is a submit button that, when pressed, will indicate that the user wants to login in under a different username and password. The following creates the form with the submit button.

```
print paragraph(
    start_form("index.php")
    , hidden_field("olduser",$PHP_AUTH_USER)
    , submit_field("newuser","Log In As New User")
    , end_form()
);
```

Using the functions described in chapter Chapter 9, this code creates a form, that, if submitted, sends the variables $olduser and $newuser back to the index.php page. When the form is submitted and the variables are sent, they will hit this portion of the authenticate.php page.

```
if (empty($PHP_AUTH_USER)
    || ( !empty($newuser) && $olduser == $PHP_AUTH_USER )
)
```

The preceding if block will test true under two conditions. First, if the user has not yet logged in, because in that case $PHP_AUTH_USER will be empty. The other condition comes from the form we just discussed. If that submit button is pressed, $newuser will not be empty and $olduser will contain the value of $PHP_AUTH_USER, meaning the user wishes to change her login name and password. If either of these is true, the following code will run:

```
{
    $what = empty($PHP_AUTH_USER) ? "login" :
        "newuser($newuser,$olduser)";
    authenticate($realm,$errmsg.":".$what);
}
```