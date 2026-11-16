The Install Wizard does not currently automatically configure Apache's httpd.conf file, so you'll probably see a dialog about this. Don't worry, we'll go through the configuration of Apache to use PHP next.

After the installation is finished, you'll be presented with a dialog declaring successful installation and an OK button. Click OK, and we'll move on to configuring Apache.

# Configuring Apache to Use PHP

We'll be configuring Apache to use PHP as a CGI under Windows, due to the instability of third party software under Windows threading. Even if you plan on going the ISAPI module route, you probably should follow these instructions and do the CGI configuration first and make sure everything works. It's much easier to switch to ISAPI module usage after everything else is working. You'll need to do a lot of stress testing under ISAPI to be sure your web server is stable.

First, make sure Apache is not running. In the PHP directory, default C:\php\, you should find a file named php4ts.dll. Windows 9x/ME users should copy it to C:\Windows\System\ while Windows NT/2000 users should copy it to C:\WinNT\System32\\.

Find the httpd.conf file, which by default is in C:\Program Files\Apache Group\Apache\conf\. Make a backup copy of this file before you edit it.

Open this file with a text editor. Use the Find menu item to search for a ScriptAlias section. It's usually in between <IfModule mod_alias.c> and </IfModule>. There may be several ScriptAlias sections, and the IfModule lines may be separated by a considerable amount of text. In the ScriptAlias section, add the following line:

```
ScriptAlias /php/ "C:/php/"
```

This tells Apache where to find the various PHP files, and creates an alias to use later on in httpd.conf to reference that directory. If you installed PHP in a non-default location, you'll need to change the path above. Don't use Windows \ in httpd.conf, use / instead.

If there doesn't seem to be any existing ScriptAlias section, add the line above directly after the <Directory...> line, which corresponds to your DocumentRoot. More explanation was provided about these in the Apache installation instructions.

Second, locate the AddType section of httpd.conf. There should already be a couple of PHP4.x lines. You can uncomment (remove the # character at the beginning) or you can type in a line below those comments:

```
AddType application/x-httpd-php .php
```

This tells Apache the files that end in .php should be treated as mime-type application/x-httpd-php. Just as GIF files are of mime-type image/gif and JPEG files are image/jpg. If there doesn't seem to be an AddType section, put this line inside the <Directory...> section as described above.

Finally, locate the Action section of httpd.conf. This typically has a couple of example Format: lines.