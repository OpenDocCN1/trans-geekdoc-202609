```
Hirdesh Bhardwaj
href='http://websjyoti.com/temp/verify.php?code=$code'>verify
your account</a> <br><br> regards, <font color='red'>automail,
webs jyoti</font> ";

$f=mail($email,$subject,$mess,$headers);
if($f == "1")
{

echo "Pls check your mail to activate your account";

}
else
{

echo " pls check mail function";
}
?>
//Verify.php
<?php

include 'db.php';

$code=$_REQUEST['code'];

mysql_query("update student set status='verified' where `code`=$code");

echo "You have been verified ";
?>
```