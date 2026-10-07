# cont'd

![](bbox=[0.155, 0.085, 0.265, 0.205])

The $errmsg variable stores any error messages when an incomplete form has been submitted. It is concatenated with the $form variable, containing the entire HTML form, then written on the page.

```
#if invalid write the error message/s and the form
if ($valid == true) { echo ($errmsg . $form); }
elelse #if the form is valid send the email
{
 $to = "php5ineasystems@hotmail.com";
 $re = "Feedback from $username";
 $msg = $comments;
 $headers = "From: $useraddr \r\n"
if( mail ($to, $re, $msg, $headers ) )
 echo("Thanks for your comments, $username");
}
?></body></html>
```

![](bbox=[0.025, 0.625, 0.125, 0.685])

This illustration shows the page after the form has been submitted without any entry input field.

| Combined Feedback Form |
| File Edit View Favorites Tools Help |
| Address | http://localhost/combined.php [Go] |
| Enter your comments... |
| Name: Bob |
| Email: bob@some-mail-server.com |
| Comments | |
| Send Form |

9. Sending email with PHP | 125