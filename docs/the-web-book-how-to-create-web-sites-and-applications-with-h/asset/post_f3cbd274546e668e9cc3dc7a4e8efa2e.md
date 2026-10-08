
This is only a test installation, so why not just click on various features and see what they do? You won't break anything. If you do, and everything goes horribly wrong, just use FileZilla to connect to the server, delete the entire Joomla folder, then upload the files again and start afresh with a new installation. So long as you click the option to delete any database tables that already exist, you won't even have to create a new database.

Let's change something in the site. Click the Front Page Manager icon, and you'll see a list of all the items that appear on the front page of the site. Click the title of the first article (Joomla community portal) and an editing screen appears:

![](img/50e1558b8202f19b96c1cc386ea5ec66_135_0.png)

This book is free of charge. To get the latest version, see www.the-web-book.com
Please do not make copies of the PDF file for others. All downloads must be from www.the-web-book.com
We can produce custom versions of this book for other web hosts. Email info@the-web-book.com for details.

![](img/50e1558b8202f19b96c1cc386ea5ec66_136_0.png)

Type some new text in place of the old story, then click the Save button at the top of the screen. Now go back to your site and you’ll see that your front page has been updated:

To sign up with the web hosting company featured in this book, please visit www.the-web-book.com/hosts.html
It costs you just the same, but brings me a small commission that funds the development of this book. Thanks!

![](img/50e1558b8202f19b96c1cc386ea5ec66_137_0.png)

As you might be starting to realise, a CMS is a hugely flexible way of working but it’s still not particularly simple. The sheer number of options and menus on the main admin screen look daunting at first. But it’s definitely worth persevering, because it will save you time in the long run. Once you’ve sorted out your design templates, you can create new pages in a flash and add them into the main body of your site in just seconds. Plus, because Joomla is very much based around templates, skins and CSS, it’s easy to roll out a new design across all of your site without having to change each individual page. So go ahead and explore Joomla.

## WordPress

Like Joomla, WordPress is a free, open source CMS. Although it is used nowadays for creating all sorts of general-purpose web sites, it was originally designed for use in blog publishing and it is in this area that it functions particularly effectively.

As with Joomla, getting an installation of WordPress up and running isn't particularly difficult. The remainder of this chapter will take you through each of the required steps in turn.

### Downloading the Software

To obtain your copy of the WordPress software, visit `www.wordpress.org` and download the .zip version of the software. At the time of writing, the latest release is version 2.7.1. If there's a later version available, use that one instead.

Once you've downloaded the file, you need to unpack the zip file. If you don't know how to do this, refer to page 128. Once you've unpacked the zip file into a separate folder, you can delete the zip file itself.

### Make a Database

Next, you need to ensure that there's a MySQL database on your web server. If you've already followed the instructions on page 124 for creating the thewebbo_cms database then it's safe to proceed. If not, go back and do that now.

### Configure WordPress

Unlike Joomla, which you configure via the web after uploading the product to your server, WordPress is slightly different. The configuration data is held in a text file which you need to edit before uploading anything.

Browse through the folder of files that was created when you extracted the zip file. In the wordpress folder you'll find a file called `wp-config-sample.php`, which you need to open. Use a text editor such as WordPad or Notepad. DO NOT use a word processor like Microsoft Word, as it will save the file as a document rather than plain text, which won't work. If you really must use a word processor, save the file by choosing Save As from the File menu, and ensure that you choose the plain text option.

With the wp-config-sample.php file open in your text editor, there are 2 sections you need to edit. First, look for this section in the file:

```
// ** MySQL settings - You can get this info from your web host **
/** The name of the database for WordPress */
define('DB_NAME', 'putyourdbnamehere');

/** MySQL database username */
define('DB_USER', 'usernamehere');

/** MySQL database password */
define('DB_PASSWORD', 'yourpasswordhere');

/** MySQL hostname */
define('DB_HOST', 'localhost');
```

Change 'putyourdbnamehere' to the name of the MySQL database you created earlier. In our case this will be 'thewebbo_cms'. Note that the single quotes need to remain in place.

Change 'usernamehere' to your web hosting username. In our case it's 'thewebbo'.

Change 'yourpasswordhere' to your web hosting password.

You can probably leave 'localhost' as it is, unless your web hosting company tells you that its MySQL database server is located on a different computer, in which case you need to enter its details here in place of localhost. It might be something like 'mysql2.yourhost.com'. But in our case, 'localhost' is what we need.

Finally, scroll down the file and locate this section:

```
/**
 * WordPress Database Table prefix.
 *
 * You can have multiple installations in one database if you give each a
 * unique prefix. Only numbers, letters, and underscores please!
 */
$table_prefix = 'wp_';
```

Note that our WordPress installation is configured to add wp_ at the start of each of the MySQL database tables it creates. That should suffice, so you can leave it alone. Just make sure that a table prefix is set, and that the WordPress prefix isn't the same as the prefix you're using for any other product that you have installed on your server. Otherwise there will be problems when table names clash and two different programs attempt to access them.

With the configuration file edited, save it to your hard disk as `wp-config.php`. Your initial WordPress configuration is now complete. Remember, you **MUST** save the file as `wp-config.php`, without the word *sample*.

### Upload The Software

You can now upload the WordPress folder from your computer to your web server. Using FileZilla, connect to the server, double-click on the `public_html` folder to open it, then right-click to create a new directory (folder) within it called `wordpress` (no capital letters). Then upload the entire contents of the WordPress folder. It will take a minute or three to transfer all of the 600 files, after which you can delete the WordPress files from your PC and exit FileZilla.

### Final Configuration

To finish setting up your installation of WordPress, open your web browser and surf to `/wp-admin/install.php` within your WordPress installation folder. So in this example, where we uploaded the files to the the-web-book.com site in the wordpress folder, the full URL will be:

```
http://www.the-web-book.com/wordpress/wp-admin/install.php
```

Note that the `public_html` folder is never part of the URL of your site. That’s where all the other folders start from.

You should now see the following screen:

![](img/50e1558b8202f19b96c1cc386ea5ec66_141_0.png)

Choose a title for your blog, and enter your email address, then click the Install WordPress button. Assuming that you edited the config file correctly, and your database host/username/password were correct, this second configuration step should only take a couple of seconds. After which, you will see a username (usually admin) and a password displayed. You'll need these in order to log into your blog to create and edit content, so make a careful note of the password.

You can now browse your blog (even though there's not much in it yet), or log into the editing system to start creating content.

To view your blog, the URL is www.yoursite.com/wordpress. To log into the editing system, use www.yoursite.com/wordpress/wp-login.php instead.

Let's create a first blog post. Log into WordPress with your username and password, and you'll see this screen:
