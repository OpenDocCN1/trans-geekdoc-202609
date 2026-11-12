missingkids.org, the Web site for the National Center for Missing and Exploited Children. But I provide more than just a link: I have a form that includes a drop-down list of all the states. If you click your state and then click Submit, you are taken to the missingkids.org site, showing the cases for your state. How did I do this? I did it all in PHP, using a combination of forms and redirects.

First, the form was simple: It's just a list of values containing the two-letter code for each state. The form's action looks like this: /kidsredir.php. Nothing fancy there. The value for the state is passed as a parameter named state. Now the magic is in the kidsredir.php file; here's the entire file:

```
```php
<?php
$state = $_GET["state"];
header("location:
http://www.missingkids.org/precreate/".$state.
".html");
?>
```
```

This file extracts the state into the $state variable and constructs a URL based on that state. And then the magic begins: This file contains no HTML code, making it safe to send headers. This file sends a header called location, which forces the browser to redirect to the given site. Thus, if you choose California in the list, you first go here:

```
http://www.jeffcogswell.com/kidsredir.php?state=CA
```

which, in turn, redirects you here:

```
http://www.missingkids.org/precreate/CA.html
```

... all thanks to the magic of the headers.

# Printing your page headers

If you want to print your page's headers and you're using PHP with Apache, you can use a handy function called apache_request_headers. Here's a sample:

```
```php
<?php
$headers = apache_request_headers();
foreach ($headers as $header => $value) {
echo "$header: $value <br />\n";
```
```

If you're using a version of PHP earlier than 4.3.0, you need to use the function getallheaders in place of apache_request_headers.