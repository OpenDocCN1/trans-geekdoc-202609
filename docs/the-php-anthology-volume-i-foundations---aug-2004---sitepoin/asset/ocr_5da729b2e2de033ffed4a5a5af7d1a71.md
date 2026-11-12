# Appendix A: PHP Configuration

This is a quick reference to configuring PHP that covers the most important general settings you need to be aware of, either when running applications in a live environment, or because they impact security or the way you write code.

# Configuration Mechanisms

The primary mechanism for configuring PHP is the php.ini file. As the master file, this provides you with control over all configuration settings. Entries generally take the format:

```
setting = value
```

Be sure to read the comments provided in the file before making changes, though. There are a few tricks, such as include_path using a colon (:) as a seperator on Unix, and a semicolon (;) on Windows.

Most Web hosts will not provide you access to your php.ini file unless you have root access to the system (which is typically not the case if you're using a cheap virtual hosting service). Your next alternative is to use .htaccess files to configure PHP (assuming the Web server is Apache).

An .htaccess file is a plain text file that you place in a public Web directory to determine the behavior of Apache when it comes to serving pages from that directory; for instance, you might identify which pages you'll allow public access to. Note that the effect of an .htaccess file is recursive—it applies to subdirectories as well.

To configure PHP with .htaccess files, your hosting provider must have the Apache setting AllowOverride Options or AllowOverride All applied to your Web directory in Apache's main httpd.conf configuration file. Assuming that is done, there are two Apache directives you can use to modify PHP's configuration:

**php_flag**
used for settings that have boolean values (i.e. on/off or 1/0) such as register_globals