# Using Basic Authentication with Apache’s .htaccess Files

You can achieve similar results to the script in Listing 16.2 without writing a PHP script.

The Apache web server contains a number of different authentication modules that can be used to decide the validity of data entered by a user. To use HTTP Basic authentication, you'll need mod_auth_basic, plus an authentication module corresponding to the password storage mechanism you plan to use. In this section, we'll look at how to store passwords in a file, and in the next section, we'll look at how to store them in a database.

To get the same output as the preceding script, you need to create two separate HTML files: one for the content and one for the rejection page. We skipped HTML elements in the previous examples but really should include `<html>` and `<body>` tags when generating HTML.

Listing 16.3, content.html, contains the content that authorized users see.
 16.4, called rejection.html, contains the rejection page. Having a page to show in case of errors is optional, but it is a nice, professional touch if you put something useful on it. Given that this page will show when a user attempts to enter a protected area it rejection might include instructions on how to register for a password, or how to get a password reset and email if it has been forgotten.

Listing 16.3 content.html—Sample Content

```
<!DOCTYPE html>
<html>
<head>
<title>Secret Page</title>
</head>
<body>
<h1>Here it is!</h1>
<p>I bet you are glad you can see this secret page.</p>
</body>
</html>
```

Listing 16.4 rejection.html—Sample 401 Error Page

```
<!DOCTYPE html>
<html>
<head>
<title>Rejected Page</title>
</head>
<body>
<h1>Go Away!</h1>
<p>You are not authorized to view this resource.</p>
</body>
</html>
```