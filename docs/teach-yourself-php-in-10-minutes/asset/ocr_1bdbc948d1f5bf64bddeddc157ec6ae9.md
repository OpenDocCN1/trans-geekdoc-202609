# Authenticating a Login

The login form, at its heart, needs to contain just two fieldsusername and password and a submit button. As long as these are present, the form's layout is up to you. For now, you can keep it fairly plain, in a simple table layout. Listing 15.1 shown the basic login form.

# Listing 15.1. A Basic Login Form

```
<FORM ACTION="login.php" METHOD="POST">
<TABLE BORDER=0>
<TR>
<TD>Username:</TD>
<TD><INPUT TYPE="TEXT" SIZE=10 NAME="username"></TD>
</TR>
<TR>
<TD>Password:</TD>
<TD><INPUT TYPE="PASSWORD" SIZE=10 NAME="password"></TD>
</TR>
</TABLE>
<INPUT TYPE=SUBMIT VALUE="Log in">
</FORM>
```

![](bbox=[0.115, 0.495, 0.16, 0.55])

> **Password Fields** The PASSWORD type input works exactly the same way as a TEXT type, but the characters entered are obscured as they are typed. The only restriction on a password field is that it cannot be given a VALUE attribute for a default value.

The form handler script, login.php , needs to check the submitted username and password values against the list of valid users. In most cases, you would check the values against a user database. You will learn about database access in PHP in Lessons 19 , "Using a MySQL Database," and 20 , "Database Abstraction," and for now you can just use a simple array of users who are permitted to use the site. Listing 15.2 shows how to do this.

# Listing 15.2. A Login Processor Script

```
<?php

session_start();

$passwords = array("chris" => "letmein",
"damon" => "thisisme",
"shelley" => "mypassword",
```