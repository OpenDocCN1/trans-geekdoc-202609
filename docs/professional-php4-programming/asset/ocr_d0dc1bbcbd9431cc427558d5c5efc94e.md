Stop and restart Apache for the altered httpd.conf file to take effect:

```
apachectl stop
apachectl start
```

Create the phpinfo.php and save it in your DocumentRoot web directory. You should then be able to see the status page from PHP at http://localhost/phpinfo.php.

If this doesn't work, review the changes --activate-module=src/modules/php4/libphp4.a caused in httpd.conf.

It may not have correctly added/altered the AddType lines as discussed in the UNIX-based installation. That's the most likely source of error. Also review the problems and solutions in the UNIX-based installation.

# # Compiling PHP Standalone

Just as in the UNIX-based installation, you should repeat PHP's configure and make steps, only without the --with-apache=... line, and then copy the resulting php program to /usr/bin/ or a suitable location.

# # Further Resources

# ## Wrox.com

If the tutorials do not produce the expected results repeatedly, there are a number of other sources to consult for more information and assistance. For all three software packages, an online discussion forum is available on the Wrox web site at: http://p2p.wrox.com/.

# ## PHP.net

These pages on the PHP web site might prove useful:

+   - http://php.net/FAQ.php. The PHP FAQ.
+   - http://php.net/funcref. Follow each link in the body and read the overview.
+   - http://www.php.net/langref. Read this whole section both before and after this book.

You also should be aware of the PHP Mailing Lists at http://php.net/support.php. These lists are archived, and most are a gateway to a newsgroup.

Most are also available in a digest mode with one big message, much less frequently, which contains all the messages since the last digest. PHP-General digest is twice daily, but is still a very large e-mail.

The PHP mailing lists are very pleasant (generally) and extremely tolerant of newbie questions, but do follow these rules:

+   - Read the manual
+   - Re-read the FAQs before you send your question