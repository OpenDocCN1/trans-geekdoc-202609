```
print br;
print $params->{'email'};
print end_html;
```

Vars is a function that returns a reference to a hash. I save this reference in the $params variable. Then I iterate through the hash using the while construct. (The each function returns the next key and value pair from the hash each time I call it.) Next, I print out the key and value pair.

Then I access the items individually. Remember, $params is a reference to a hash; it's not a hash itself. I have to use $params->{'name'}; (not $params['name']) to access the individual elements.

The preceding example works with both the HTTP-GET and HTTP-POST methods of sending data from a form. Suppose you save the preceding code as cgipm4.pl (which is what I call it on the accompanying CD-ROM). Then you can use this script in response to either of the forms in the sections “Reading from an HTTP-GET” and “Reading from an HTTP-POST,” earlier in this chapter. In both cases, change the action parameter of the form tag to action=”/cgi-bin/cgipm4.pl”.

# Displaying Errors and Warnings

If you write a CGI script that has errors in it, you receive a rather foreboding message such as this:

Internal Server Error
The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator,
webmaster@cogswell.biz and inform them of the time the error occurred, and anything you might have done that may have caused the error.
More information about this error may be available in the server error log.

When you see this error, you can look in the error.log file found in the logs directory under the main Apache installation. But I have a better way of finding out the errors.

First, to display errors right on the Web page, add this code to the beginning of your CGI script, after the pound-bang line: