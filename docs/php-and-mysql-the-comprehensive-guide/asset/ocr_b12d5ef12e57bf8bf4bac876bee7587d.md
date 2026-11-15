![](bbox=[0.145, 0.102, 0.915, 0.365])

Figure 33.3 Basic Authentication Is Activated

# ## 33.3 HTTP Authentication by Hand

Not leaving HTTP authentication to the server has several advantages:

+   - You don't have to fiddle with a text file or use Apache's not-so-simple database functions, but can instead control everything with PHP.
+   - Compared to IIS, you have the advantage that you do not have to work with user accounts.
+   - You can work (relatively) independently of the web server.

HTTP authentication is quick to implement. Do you remember what happens at the beginning of HTTP authentication? The browser receives HTTP message 401, which you can output using PHP:

```
header("WWW-Authenticate: Basic realm=\"Application XY PHP\"");
header("HTTP/1.1 401 Unauthorized");
```

> **Note**
> 
> Caution: In some configurations, especially in connection with IIS, the preceding lines do not work! In this case, a slightly modified HTTP header often helps:
> 
> header("WWW-Authenticate: Basic realm=\"Application XY PHP\"");
> header("Status: 401 Unauthorized");

The query appears (see Figure 33.4), but of course there is still no password check. You have access to the user name and password via the $_SERVER environment variable and then with $_SERVER["PHP_AUTH_USER"] and $_SERVER["PHP_AUTH_PW"]. This allows a