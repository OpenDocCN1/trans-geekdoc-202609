Add the following line in the Action section:

```
Action application/x-httpd-php "/php/php.exe"
```

This tells Apache that a file whose mime-type is application/x-httpd-php, which we defined with
the AddType above, should be acted upon by the file named php.exe which is located in the directory
defined by the ScriptAlias "/php/" that we typed above.

Once again, if there doesn't seem to be an Action section in your httpd.conf, simply add this inside
the Directory section as above. Review the lines you have added for typing errors. While they are
spread throughout the httpd.conf file to keep them organized by their command, these three lines act
together to tell Apache how to cope with PHP files.

You may want to alter that second line so that files ending in .php3 (older scripts you may find) or
even .htm and .html files are passed through PHP. Forcing all HTML files through PHP will not slow
down the response time appreciably. Also, including older extensions will allow you to add PHP
features in all sorts of places in existing HTML files, without having to re-link to your web site. It also
allows the use of .htm or .html which users are used to, instead of .php.

Your AddType line may end up looking like this:

```
AddType application/x-httpd-php .php .htm .html .php3
```

The order of the file endings is irrelevant, and you can add as many as you like that make sense. For
example, it usually doesn't make a lot of sense to pass .mp3 files through PHP. In fact, that will
probably break your MP3 URLs, since PHP will add some default headers.

Once you've made and reviewed all your changes, save the httpd.conf file, and restart Apache.

# What Can Go Wrong?

If Apache doesn't start at this point, review the three lines you added for typing errors. Also make sure:

+   That you have the correct directory for your PHP installation in the ScriptAlias line.

+   That you used / instead of \\ in that path.

+   That the mime-type application/x-httpd-php is the same on both the AddType and the
+   Action lines. Copy and paste the two, so you are sure they are the same.

+   That php.exe actually is in the right directory.

+   That you copied php4ts.dll into your Windows system directory.

If you've double-checked all the above, and stopped/restarted Apache and it still doesn't work, review
the What Can Go Wrong? section under Installing Apache. In particular, check the error logs and the MS
DOS console window for errors.

If all else fails, try copying php4ts.dll into the same directory as the php.exe file. By all rights,
Windows is supposed to be able to find it in the system directory and load it, but if not, PHP can
probably find it if it's sitting in the same directory as the php.exe file.