
```
</ul>
</div>
<div class="page">
<div class="content">
```

- 3. Create a new file to be named header.html and stored in the includes directory.
- 4. Paste in the copied code.
- 5. Save the file.

## Adding Dynamic Functionality to the Header

The next series of steps add dynamic functionality to the HTML template by incorporating PHP within the HTML. You'll want to do this for anything that might change on a page-by-page basis or otherwise won't be static. For the header file, there are two areas that should be dynamic: the page title and the highlighting of the top navigation link (see the first tab in Figure 3.7).

- 1. In header.html, use an if-else clause to define the page title:

```
<title><?php if (isset($page_title)) {
echo $page_title;
} else {
echo 'Knowledge is Power: And It Pays to Know';
}
?></title>
```

The page's title shows at the top of the browser window, in bookmarks, and in the browser's history; it should be different from one page to the next. The aptly named $page_title variable will be available to the header file to represent that value. However, proper programming says that you shouldn't assume that the variable exists. So this code first checks if that variable is set (that is, has a value). If it is, that value will be printed as the page's title. If $page_title is not set, a default title will be used.

- 2. Remove the list items (between the opening and closing MENU comments) that constitute the top navigation tabs.

The navigation tab for the currently viewed page has a specific CSS class applied to it, which changes how it appears. You could use JavaScript to create this effect, but for easy, all-browser compatibility, I'll make this happen in PHP.

- 3. In place of the list items, begin a PHP code block:

```php
<?php
```

- 4. Create an array of pages:

```php
$pages = array(
    'Home' => 'index.php',
    'About' => 'about.php',
    'Contact' => 'contact.php',
    'Register' => 'register.php'
);
```

This array represents the main navigation items. The key for each element is the text to be displayed on the tab. The value for each element is the corresponding page (that is, what page that tab will be linked to).

> > A few of the pages linked in the header and footer won't actually be created in this book but will be quite easy for you to create, when necessary.

- 5. Determine which page is currently being viewed:

```php
$this_page = basename($_SERVER['PHP_SELF']);
```

In order to dynamically apply a class to the current page, the script needs to know what the current page is, which happens to be the value PHP assigns to $_SERVER['PHP_SELF']. If the user is viewing http://www.example.com/dir/file.php, then $_SERVER['PHP_SELF'] will have a value of /dir/file.php. To get just the file.php part of that, the basename() function is applied.

- 6. Loop through each page:

```php
foreach ($pages as $k => $v) {
    echo '<li>';
}
```

This loop will run once for each item in the array. Within the loop, the $k and $v values can be used to create the navigation tabs. The first line of code within the loop begins a new HTML list item.

> > I generally recommend that programmers use curly brackets for all conditionals. When you don't, like when I'm saving space in this book, place the entire construct on one line to be clear, as in Step 7.

- 7. Add the class if it's the current page:

```php
if ($this_page == $k) echo ' class="selected"';
```

The current page needs to use the HTML: <li class="selected">. This code will do that.

- 8. Complete the list item started in Step 6:

```php
echo '><a href="' . $v . '"><span>' . $k . '</span></a></li>';
```

First the opening <li> tag is closed. Then a link is created to the specific page, represented by $v. Next, the displayed text is written within <span> tags, and the link and list item tags are completed. The echo statement

tip
Have your PHP code create tidy HTML output in case you need to examine it.

concludes on the next line so that a newline is added to the HTML source of the page (Figure 3.10).

```
<!-- MENU -->
<li class="selected"><a href="index.php"><span>Home</span></a></li>
<li><a href="about.php"><span>About</span></a></li>
<li><a href="contact.php"><span>Contact</span></a></li>
<li><a href="register.php"><span>Register</span></a></li>
<!-- END MENU -->
```

Figure 3.10

- 9. Complete the foreach loop and the PHP code block:

```php
} // End of FOREACH loop.
?>
```

To be clear, this closing PHP tag is required, because this closes a PHP block dropped within a larger body of HTML.

- 10. Save the file.

That's it for the header.

## Creating the Footer

The footer takes over after the page-specific content. It creates the sidebar items, and the page footer (such as the copyright and other tertiary links), and completes the HTML page.

- 1. Open the designed template file in your text editor or IDE, if it is not already.

- 2. Copy all the HTML from the template file, from the page-specific content to the end, like so:

```
</div>
<div class="sidebar">
<!-- SIDEBAR -->
<div class="title">
<h4>Manage Your Account</h4>
</div>
<ul>
<li><a href="renew.php" title="Renew Your Account">Renew Account</a></li>
<li><a href="change_password.php" title="Change Your Password">Change Password</a></li>
<li><a href="favorites.php" title="View Your Favorite Pages">Favorites</a></li>
<li><a href="recommendations.php" title="View Your Recommendations">Recommendations</a></li>
<li><a href="logout.php" title="Logout">Logout</a></li>
</ul>
<div class="title">
<h4>Content</h4>
</div>
<ul>
<li><a href="category.php?id=3" title="Common Attacks">Common Attacks</a></li>
<li><a href="category.php?id=5" title="Database Security">Database Security</a></li>
<li><a href="category.php?id=1" title="General Web Security">General Web Security</a></li>
<li><a href="category.php?id=4" title="JavaScript Security">JavaScript Security</a></li>
<li><a href="category.php?id=2" title="PHP Security">PHP Security</a></li>
<li><a href="pdfs.php" title="PDF Guides">PDF Guides</a></li>
</ul>
<!-- END SIDEBAR -->
</div>
<div class="footer">
<p><a href="site_map.php" title="Site Map">Site Map</a> | <a href="policies.php" title="Site Policies">Policies</a> &nbsp;&nbsp; &copy; Knowledge is Power | Design by <a href="http://www.spyka.net">spyka webmaster</a></p>
</div>
<!-- END PAGE -->
</div>
</body>
</html>
```

That's the footer code for a logged-in, non-administrative user. In the next series of steps, the code for the other two possible situations (a visitor who is not logged in and an administrator who is logged in) are changed.

- 3. Create a new file to be named footer.html and stored in the includes directory.

- 4. Paste in the copied code.

- 5. Save the file.

### Adding Dynamic Functionality to the Footer

Now you need to do to the footer file what you did to the header: Use PHP to dynamically generate some HTML. There are two alterations to make. First, the sidebar should show the login form if the user is not logged in, account links if they are, and also administrative links if they're logged in and are an administrator. Second, you can dynamically pull the list of categories from the database.

- 1. In footer.html, in lieu of the Manage Your Account links, begin an if-else conditional:

```php
<?php
if (isset($_SESSION['user_id'])) {
```

The page will know that the user is logged in if $_SESSION['user_id'] is set.

- 2. Recreate the Manage Your Account links using PHP:

```php
echo '<div class="title">'
<h4>Manage Your Account</h4>
</div>
<ul>
<li><a href="renew.php" title="Renew Your Account">Renew Account</a></li>
<li><a href="change_password.php" title="Change Your Password">Change Password</a></li>
<li><a href="favorites.php" title="View Your Favorite Pages">Favorites</a></li>
<li><a href="recommendations.php" title="View Your Recommendations">Recommendations</a></li>
<li><a href="logout.php" title="Logout">Logout</a></li>
</ul>
';
```

This PHP code creates the same links as in the original template. Two of these linked pages will be created in subsequent chapters. The closing single quote ends on its own line in order to create a newline in the HTML source.
