In a moment you will manually add some code. so you need to make space for it.
Notice that you're adding the code before the HTML document proper, which
begins with the <html> element. Server code is often placed outside the HTML
document, which makes it easier to find and edit. And don't forget: When the page
is output from the server to the client, the server code is stripped out, so users will
never see this code.

> NOTE In PHP, any time you attempt to send content back to the browser via a header—
> and setting cookies is one example of this—you must add this script before the first line of
> XHTML code, or you will see an error along the lines of “cannot add header information.”
> The simple solution to this problem is to put such content at the very beginning of the file.

# 3) Type the code block below, as appropriate.

In ASP:

```
<%
Response.Cookies("firstName") = Request.QueryString("firstName")
Response.Cookies("firstName").Expires = Date+30
Response.Cookies("lastName") = Request.QueryString("lastName")
Response.Cookies("lastName").Expires = Date+30
%>
```

In ColdFusion:

```
<cfcookie name="firstName" expires="never" value="#url.firstName#">
<cfcookie name="lastName" expires="never" value="#url.lastName#">
```

In PHP:

```
<?php
setcookie('firstName', $_GET['firstName'], time() + (60*60*24));
setcookie('lastName', $_GET['lastName'], time() + (60*60*24));
?>
```

![](bbox=[0.26, 0.67, 0.92, 0.87])