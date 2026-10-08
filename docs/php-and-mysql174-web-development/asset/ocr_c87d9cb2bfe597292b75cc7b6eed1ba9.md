# Creating a Sample Application: Smart Form Mail 103

```
$toaddress = "feedback@example.com";
```

```
$subject = "Feedback from web site";
```

```
$mailcontent = "Customer name: ".filter_var($name)."\n"
"Customer email: ".$.email."\n"
"Customer comments: "\n".$feedback."\n";
```

```
$fromaddress = "From: webserver@example.com";
```

```
//invoke mail() function to send mail
mail($toaddress, $subject, $mailcontent, $fromaddress);
```

```
?
<!DOCTYPE html>
<html>
<head>
<title>Bob's Auto Parts - Feedback Submitted</title>
</head>
<body>
<h1>Feedback submitted</h1>
<p>Your feedback has been sent.</p>
</body>
</html>
```

Generally, we should check that users have filled out all the required fields using, for example, isset(). We have omitted this function call from the script and other examples for the sake of brevity.

In this script, we can see how concatenated the form fields and use PHP's mail() function to send them to feedbackexample.com. This is a sample email address. If you want to test the code in this chapter, substitute your own email address here. Because we haven't used mail(), we need to discuss how it works.

Unsurprisingly, this function sends The prototype for mail() looks like this:
bool mail(string to, string subject, string message, string [additional_headers], string [additional_parameters]);

The first three parameters are compulsory and represent the address to send to, the subject line, and the message contents, respectively. The fourth parameter can be used to send any additional valid email headers. Valid email headers are described in the document RFC8222, which is available online if you want more details. (RFCs, or Requests for Comment, are the source of many Internet standards; we discuss them in Chapter 18, "Using Network and Protocol Functions") Here, the fourth parameter adds a From: for the mail. You can also use it to add Reply-To: and Cc: fields, among others. If you want more than one