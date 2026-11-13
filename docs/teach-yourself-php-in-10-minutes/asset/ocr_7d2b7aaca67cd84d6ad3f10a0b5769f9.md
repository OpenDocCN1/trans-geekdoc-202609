If no expires attribute is sent in the Set-Cookie header, the cookie will be destroyed when the web browser is closed.

The other attributes that can be set are the domain name and the path by which a browser will send back a cookie. When you make any subsequent visit to a page for which you have a cookie set, its name and value are sent to the web server.

The default behavior is to send a cookie back to any page on the same domain that it was set from. By setting the domain and path, you can tell the cookie to be sent back to other subdomains or only to scripts in a certain part of the site.

The following header creates an email cookie that is sent back to any subdomain of lightwood.net, as long as the page requested is in the /scripts subdirectory:

```
Set-Cookie: email=chris@lightwood.net; domain=.lightwood.net;
path=/scripts
```

**Subdomains** You can only set the domain attribute of a cookie to a variant of the domain from which the cookie was originally set, or to .yourdomain.com to indicate all subdomains.

This is a security measure to prevent some websites from being able to confuse others. For example, you cannot set a cookie that would be sent back to www.php.net from any website that is not hosted at php.net .

# Accessing Cookies

The $_COOKIE super-global array in PHP contains all the cookies that have been sent to the current script. Cookies are sent back to the web server in an HTTP header, and PHP builds the $_COOKIE array based on this information.

You can access cookies in the same way that you reference posted form data. For example, the following statement displays the current value of the email cookie:

```
echo $_COOKIE["email"];
```

If you ever feel that your cookies are getting in a bit of a mess, you can just create a script to dump them all out to screen so you can see what's going on. It is as simple as this:

```
echo "<PRE>";
print_r( $_COOKIE );
```