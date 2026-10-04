# Handling and Avoiding Errors

![](bbox=[0.15147, 0.09375, 0.91755, 0.5363300000000001])

Figure 8-2

The full code will look like this:

```
<<?
function e_mail_admin($error_no, $error_output, $full_date, $full_time, $request_page)
(
    $to = "Administrator <admin@yourdomain.com>";

    $subject = "Apache Error Generation";

    $body = "<html>";
    $body .= "<head>";
    $body .= "<title></title>";
    $body .= "</head>";
    $body .= "<body>";
    $body .= "Error occurred on <b>" . $full_date . "</b> at <b>" . $full_time . "</b></body><br>";
?>
```

221