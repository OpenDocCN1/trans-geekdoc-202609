# 2. WRITING YOUR FIRST PHP SCRIPT

Then write out the changes using the ^O (control plus capital letter O) “Write Out” command (ctrl+O). Next, press the return key to confirm the name of the file to write out. Finally, exit nano using the ^X Exit command (ctrl+X). See Figure 2.18.

![](bbox=[0.499, 0.103, 0.869, 0.173])

In the terminal window, type the following command to restart Apache for these changes to stick:

```
```bash
sudo systemctl restart apache2
```
```

# Installing the Database Management Tool Adminer

Next, we’re going to install a web-based database management tool. There are a few out there, the most popular being phpMy-Admin[1]. However, I like to use one called Adminer because it is contained in a single PHP file, runs faster, and has a reputation for having greater security.

![](bbox=[0.499, 0.337, 0.869, 0.509])

Open up a browser and navigate to the Adminer Download Page[2]. From there, select the latest version of Adminer for MySQL as in Figure 2.19.

Doing so downloads the Adminer PHP file to your Downloads folder.

Next, we need to rename this file index.php and copy it somewhere into our html/ folder where Apache serves up our web pages. The root of our html/ folder is located in the directory /var/www/html. The best way to do this is by using the terminal window.

In the terminal window cd to the /var/www/html directory by typing:

```
```bash
cd /var/www/html
```
```

The output of the command is shown in Figure 2.20.

![](bbox=[0.499, 0.728, 0.869, 0.801])

[1] phpMyAdmin: https://www.phpmyadmin.net/

[2] Adminer Download Page: https://www.adminer.org/#download