# Using gettext() in an Internationalized Application

To enable gettext() and related functions in PHP, after you have installed GNU gettext on your server, you requires reconfiguring and recompiling PHP on a Linux or Mac OS system, enabling a pre-built extension on a Windows system. When configuring PHP for compiling on Linux or Mac OS X, add the following configuration flag:

```
--with-gettext
```

After this compilation flag, continue compiling and installing PHP as usual. Remember to restart Apache after the new build the PHP module has been installed.

On Windows, edit your php.ini file to enable the php_gettext.dll by removing the semicolon from the line that looks like this:

```
;extension=php_gettext.dll
```

Restart the Apache server after the change you have made and this saved file. With the appropriate changes to your system as indicated above, you should now see a new section in the results of the phpinfo() function that indicate GNU gettext support is enabled.

With GNU gettext enabled, the next change is to create directories for your local-specific content within the document root of your web server. First, you will need to create a directory in the document root that will contain all the locale directories (for all the locales you want to support).

Next, within your project, the locale directories should be named according to the two-letter abbreviation of the language according to the ISO-639-I specification (e.g., "en", "ja", "de") by an underscore, for example a two-letter uppercase country code according to the ISO-3166-1 (e.g., "US", "JP", "DE"). Within the locale-specific directory should be a directory LC_MESSAGES.

So, to handle three locales in your system using GNU gettext and the PHP gettext() function, your directory structure might look something like this:

```
/htdocs
  /de_DE
    /LC_MESSAGES
  /en_US
    /LC_MESSAGES
  /ja_JP
    /LC_MESSAGES
```

Next, you'll learn what sorts of files go into these directories—they're not PHP files, but rather files that contain the translated strings to be used throughout the localized web site.

# Creating Translation Files

The translation files stored in the filesystem as above and by GNU gettext are a specific type of file called Portable Object File, or PO file. These files are plain text, but have the extension *.po. While the use of a specific editor is not required to create PO files—they are just plain text after all—many people find the use of an editor or content management tool