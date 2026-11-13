phpMyAdmin will then be available through your Web server via a URL like the following: http://localhost/phpMyAdmin-2.5.1-rc3/

On Windows, you'll use a zip utility like WinZip or pkzip to unzip the files.

Before you can access the application, you'll need to make changes to the config.inc.php file. In most cases, all you'll need to do is put the appropriate username and password on the following lines:

```
$cfg['Servers'][$i]['user']     = 'root';     // MySQL user
$cfg['Servers'][$i]['password'] = 'myypass';  // MySQL
password
```

If you're finding an error that states you don't have iconv support compiled in, simply change the following entry in the config.inc.php file to FALSE.

```
$cfg['AllowAnywhereRecoding'] = TRUE
```

Once you are done with the configuration you should be able to go to the /index.php page and start using phpMyAdmin.

Using phpMyAdmin is fairly straightforward, and we won't explain it here. Just spend some time clicking around and you'll get a good idea of how it works. Figures 2-1 and 2-2 show what you can expect from a couple of phpMyAdmin's screens.

![](bbox=[0.09, 0.53, 0.75, 0.9])

Figure 2-1: View of a table in phpMyAdmin