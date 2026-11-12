```
NameVirtualHost *

<VirtualHost *>
ServerName www.mysite.com
DocumentRoot /usr/local/apache/htdocs/mysite
</VirtualHost>

<VirtualHost *>
ServerName www.mysite2.com
DocumentRoot /usr/local/apache/htdocs/mysite2
</VirtualHost>
```

When Apache receives a request on any IP address, it treats the request as a request for a virtual host because the NameVirtualHost directive specified *; meaning all IP addresses. Apache looks through all the virtual host blocks identified with * to find a match for the server name received in the request. When it finds a match, it uses the directives included for that virtual host. If it can’t find a match for the server name in any of the virtual host ServerName directives, it uses the first virtual host block in the configuration file, treating the first virtual host definition as the default.

Here are a few additional points to remember about virtual host blocks:

+   * Directives used outside the virtual host block are in effect unless they’re overridden by a directive inside the virtual host block.
+   * You can use almost any directive in a virtual host block.
+   * You can set up a different e-mail address for the server administrator and configure different log files.
+   * You can set up different CGI directories.
+   * You can use Directory and File directives inside a virtual host.
+   * You can use different access directive settings. Your virtual hosts are almost completely independent, and you can set up each one differently from the others.