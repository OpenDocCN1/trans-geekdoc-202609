# FIGURE 13.10 Simple login and redirection

![](bbox=[0.32, 0.08, 0.7, 0.5])

Let's create a simple page to illustrate redirection:

```
<?php
// File: example13-26.php
if(isset($_POST["submit"])) {
    $strUserPass = array ( "john" => "red",
        "simon" => "green",
        "liz" => "blue",
        "david" => "yellow");
    if (array_key_exists($_POST["strUsername"], $strUserPass) )
        if ($strUserPass[$_POST["strUsername"] ] ==
            $_POST["strPassword"])
            header("location: example13-27.php");
        else
            echo "<h1>Incorrect Username and/or password!</h1>";
}
?>
<form name="form1" method="post" action="">
<p>
<label for="strUsername">Username: </label>
<input type="text" name="strUsername" id="strUsername"/></p>
<p>
<label for="strPassword">Password: </label>
```