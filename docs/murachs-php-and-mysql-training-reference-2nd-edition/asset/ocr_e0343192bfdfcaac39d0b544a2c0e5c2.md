# How to configure phpMyAdmin

XAMPP includes a web-based tool for working with MySQL named phpMyAdmin. By default, phpMyAdmin stores the username and password for MySQL’s root user in its configuration file, which is a plain text file. Since this isn’t secure, it’s generally considered a good practice to modify these default settings.

We recommend changing the authentication type for phpMyAdmin from ‘config’ to ‘cookie’ as shown in figure C-4. When you use the ‘cookie’ authentication type, phpMyAdmin does not store any usernames or passwords in its configuration file. Instead, it prompts the user for a username and password when it starts, and it stores the username and password in a cookie in the user’s browser.

Once you’ve modified the configuration file for phpMyAdmin, you can use the second procedure in this figure to make sure the MySQL server is working correctly and to make sure that phpMyAdmin is configured correctly.