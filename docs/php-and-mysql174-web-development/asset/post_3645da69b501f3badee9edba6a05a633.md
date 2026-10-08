
Using require () and include () 135

existing page, cuts out the existing text from the middle of the file, enters new text, and saves
the file under a new name.

![](img/654520c37415debd4290b9b4aa2c03f2_166_0.png)

Figure 5.2 TLA Consulting has a standard look and feel for all its web pages

Consider this scenario: The website has been around for a while, and the company now has
tens, hundreds, or even thousands of pages all following a common style. A decision
is made to change part of the standard look; the change might be something minor, such as adding an email address to the footer of each page or adding a single new entry to the navigation-menu. Do you want to make that minor change on tens, hundreds, or even thousands of
pages?

Directly reun the sections of HTML common to all pages is a much better approach than
cutting and pasting on tens, hundreds, or even thousands of pages. The source code for
the home page (home.html) shown in Figure 5.2 is given in Listing 5.1.

# Listing 5.1 home.html—The HTML That Produces TLA Consulting's Home Page

```html
<!DOCTYPE html>
<html>
<head>
<title>TLA Consulting Pty Ltd</title>
<link href="styles.css" type="text/css" rel="stylesheet">
</head>
<body>
```

```html
<!-- page header -->
<header>
  <img src="logo.gif" alt="TLA logo" height="70" width="70" />
  <h1>TLA Consulting</h1>
</header>

<!-- menu -->
<nav>
  <div class="menuitem">
    <a href="home.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Home</span>
    </a>
  </div>

  <div class="menuitem">
    <a href="contact.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Contact</span>
    </a>
  </div>

  <div class="menuitem">
    <a href="services.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Services</span>
    </a>
  </div>

  <div class="menuitem">
    <a href="about.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">About</span>
    </a>
  </div>
</nav>

<!-- page content -->
<section>
  <h2>Welcome to the home of TLA Consulting.</h2>
  <p>Please take some time to get to know us.</p>
  <p>We specialize in serving your business needs and hope to hear from you soon.</p>
</section>
```

Using require() and include () 137

```html
<!-- page footer -->
<footer>
<p>&copy; TLA Consulting Pty Ltd.<br />
Please see our
  <a href="legal.php">legal information page</a></p>
</footer>
</body>
</html>
```

You can see in Listing 5.1 that a number of distinct sections of code exist in this file. The HTML-<head> element links to the cascading stylesheet (CSS) definitions used by the page. The section labeled "page header" displays the company name and logo, "menu" creates the page's navigation bar, and "page content" is text unique to this page. Below that the footer page. You can usefully split this file and name the parts header.php, home.php, and footer.php. Both header.php and footer.php contain code that will be reused on other pages.

The file home.php is a replacement for home.html and contains the unique page content and two require() statements shown in Listing 5.2.

# Listing 5.2 home.php—The Page Produces TLA's Home Page

```php
<?php
require('header.php');
?>
<!-- page content -->
<section>
  <h2>Welcome to the home of TLA Consulting.</h2>
  <p>Please take some time to get to know us.</p>
  <p>We specialize in serving your business needs and hope to hear from you soon.</p>
</section>
<?php
require('footer.php');
?>
```

The require() statements in home.php load header.php and footer.php. As mentioned previously, the name given to these files does not affect how they are processed when you call them with require(). A common convention is to call partial files inc (here, inc stands for include). This is not recommended as a general strategy, as .inc files will not be interpreted as PHP unless the web server has been configured specifically for this. If you're going to do this, you should place your include files in a directory that is be seen by scripts outside the web document. This setup is a good strategy because it prevents the files from being loaded individually, which would either (a) produce some errors if the file extension is .php but contains only a partial page or (b) allow people to read your source code if you used another extension.

The file header.php contains the CSS definitions that the page uses, the tables that display the company name, and navigation menus, as shown in Listing 5.3.

# Listing 5.3 header.php—The Reusable Header for All TLA Web Pages

```html
<!DOCTYPE html>
<html>
<head>
<title>TLA Consulting Pty Ltd</title>
<link href="styles.css" type="text/css" rel="stylesheet">
</head>
<body>
<!-- page header -->
<header>
  <img src="logo.gif" alt="TLA logo" height="70" width="70" />
  <h1>TLA Consulting</h1>
</header>

<!-- menu -->
<nav>
  <div class="menuitem">
    <a href="home.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Home</span>
    </a>
  </div>

  <div class="menuitem">
    <a href="contact.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Contact</span>
    </a>
  </div>

  <div class="menuitem">
    <a href="services.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">Services</span>
    </a>
  </div>

  <div class="menuitem">
    <a href="about.html">
      <img src="s-logo.gif" alt="" height="20" width="20" />
      <span class="menutext">About</span>
    </a>
  </div>
</nav>
```

The file footer.php contains the table that displays the footer at the bottom of each page. This file is shown in Listing 5.4.

# Listing 5.4 footer.php—The Reusable Footer for All TLA Web Pages

```html
<!-- footer -->
<footer>
<p>&copy; TLA Consulting Pty Ltd.<br />
Please see our
  <a href="legal.php">legal information page</a></p>
</footer>

</body>
</html>
```

This approach gives you a consistent-looking website very easily, and you can make a new page in the same style by typing something like this:

```php
<?php require('header.php'); ?>
Here is the content for this page
<?php require('footer.php'); ?>
```

Most importantly, after you have created many pages using this header and footer, you can easily change the header and footer files. Whether you are making a minor text change or completely redesigning the look of the site, you will need to make the change only once. You do not need to separately every page in the site because each page is loading in the header and footer files.

The example shown here uses only HTML in the body, header, and footer. This need not be the case. Within these files, you could use PHP statements to dynamically generate parts of the page.

If you want to be sure that a file will be treated as plain text or HTML, and not have any PHP, you may want to use readfile() instead. This function echoes the content of a file without parsing it. This can be an important safety precaution if you are using user-provided text.

# Using auto_prepend_file and auto_append_file

If you want to use require() or include() to add your header and footer to every page, you can do it another way. Two of the configuration options in the php.ini file are auto_prepend_file and auto_append_file. By setting these options to point to the header and footer files, you ensure that they will be loaded before and after every page. Files included using these directives behave as they had been added using include statement; that is, if the file is missing, a warning will be issued. For Windows, the settings look like:

```ini
auto_prepend_file = "c:/path/to/header.php"
auto_append_file = "c:/path/to/footer.php"
```

For Unix, like this:

```ini
auto_prepend_file = "/path/to/header.php"
auto_append_file = "/path/to/footer.php"
```
