# Part I: Getting Up and Running with PHP

+   2. Look for the Loaded Configuration File entry toward the top of the testing.php page. This is the path to the php.ini file that is used to configure your PHP engine.

+   3. Open this file in a text editor, such as Notepad (Windows), TextEdit (Mac), or Text Editor (Ubuntu).

You may need root (administrator) to access this file. If you don't have administrator access, ask your server administrator to set the time zone for you.

+   4. Search for the line in the file:
;date.timezone =

If for some reason this isn't in your php.ini file, simply add it.

+   5. Remove the semicolon from the start of the line, and add your server's time zone after the equals sign at the end. Find your time zone in the file at http://www.php.net/timezones. For, if your server resides in Los Angeles, you'd change the line to:

date.timezone = America/Los_Angeles

+   6. Save the file and quit your editor.

+   7. Restart Apache using the method appropriate for your installation. For example, on Ubuntu the System < Administration Services as described earlier in the chapter; or on Windows Choose All Services from the WampsServer icon; and on the Mac run the /Applications/MAMP/MAMP application and click Start Servers, followed by Start Servers.

+   8. To test the setting working, reload the testing.php script and look for the date.timezone entry. It should now show the time zone that you set in Step 5, as the Default timezone entry further up the page. All done!

If you (can't want to) edit your php.ini file, you have other ways to set your time zone:

+   Create an .htaccess file in the document root of your Web site) and add a directive to set your time zone:

```
php_value date.timezone America/Los_Angeles
```

+   Alternatively, to set the start of each PHP script that you create, add a line to this:

```
date_default_timezone_set( "America/Los_Angeles" );
```

You can find out more about configuring PHP, including the php.ini file and .htaccess files, in Appendix B.

# Other Ways to Run PHP

This chapter has concentrated on the easiest way to get PHP up and running on your computer. You've looked at the Apache, PHP, and MySQL packages on Ubuntu, installing a complete Apache/PHP/MySQL setup on Windows using WampsServer, and doing the same on the Mac using MAMP.

You can run PHP in a few other ways. The following sections take a quick look at them.