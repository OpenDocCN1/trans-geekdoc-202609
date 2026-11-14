
## 3. Display administration options, if the user is also an administrator:

```php
if (isset($_SESSION['user_admin'])) {
    echo '<div class="title">
<h4>Administration</h4>
</div>';
<ul>
<li><a href="add_page.php" title="Add a Page">Add Page</a></li>
<li><a href="add_pdf.php" title="Add a PDF">Add PDF</a></li>
<li><a href="#" title="Blah">Blah</a></li>
</ul>
';
}
```

If the user is logged in and is of type admin, they should get extra options. This code will create a secondary panel of links in the sidebar. You'll develop the add_page.php and add_pdf.php scripts in Chapter 5.

## 4. Complete the primary conditional:

```php
} else {
    require ('includes/login_form.inc.php');
}
?>
```

The else clause applies if the user's not logged in. In that case, the login form should be displayed instead of any account links. To keep the code tidy, the login form will be written in a separate file that you'll develop in the next chapter.

## 5. In place of the static HTML category links, dynamically generate them:

```php
<?php
$q = 'SELECT * FROM categories ORDER BY category';
$r = mysqli_query($dbc, $q);
while (list($id, $category) = mysqli_fetch_array($r, MYSQLI_NUM)) {
    echo '<li><a href="category.php?id=' . $id . '" title="' . $category . '">' . $category . '</a></li>';
}
?>
```

This is basic PHP and MySQL: A query is run, its results are fetched, and one list item is created for each returned record. The links pass along the category ID in the URL that will be used by category.php, which you'll write in Chapter 5.

> **tip**
> If you want to test how the site comes together, prior to creating the login form file, just comment out the line that includes it (in Step 4).

> **note**
> If your content categories aren't likely to change often, it'd be better to hardcode the category links as HTML and save yourself the overhead of the extra database query.

The link to the PDFs page is separate because that's not a content category in the database.

- 6. Save the file.

And that's it for the footer.

## Creating the Home Page

To put it all together, you'll create the home page, which will combine the four files—configuration, header, MySQL connection, and footer—into one complete page.

- 1. Create a new PHP script in your text editor or IDE to be named index.php and stored in the Web root directory.

![](img/4f47e47c67bd619ac73250f11c9fc7ce_86_0.png)

## note

The parentheses with require and include aren't required, but you'll see me use them in this book.

- 2. Include the configuration file:

```php
<?php
require('./includes/config.inc.php');
?>
```

The config file defines system settings, handles errors, and starts the session, so it should always be the first (noncomment) code in your pages.

- 3. Include the header file:

```php
include('./includes/header.html');
```

- 4. Require the database connection:

```php
require(MYSQL);
```

![](img/4f47e47c67bd619ac73250f11c9fc7ce_86_1.png)

## note

In the downloadable version of index.php, you'll see a bit of extra code, which you'll add in Chapter 4.

The database connection script can be included by referring to the MYSQL constant, defined in the configuration file. This means that even if you change the name or location of mysqli.inc.php, you have to change only one line in the configuration file and all your pages will still include that script properly.

In this particular version of the home page, the database connection isn't needed until the footer, but most pages will need it before the page-specific content.

- 5. Create the page-specific content:

```php
?> <h3>Welcome</h3>
<p>Welcome to Knowledge is Power, a site dedicated to keeping you up to date on the Web security and programming information you need to know. Blah, blah, blah. Yadda, yadda, yadda.</p>
```

- 6. Include the footer file:

```php
<?php
include('./includes/footer.html');
?>
```

- 7. Save the file.

- 8. Load the file in your Web browser to test the result.
Since this is PHP, you must run index.php through a URL (such as http://something), not through file://.

- 9. To test what it looks like when logged in, add this line after including the configuration file:
```php
$_SESSION['user_id'] = 1;
```

- 10. To test what the page looks like when logged in as an administrator, add the following line of code after including the configuration file:
```php
$_SESSION['user_type'] = 'admin';
```

## REQUIRE AND INCLUDE

In the home page, I use both require and include to bring in the four scripts. These two control structures (they're not technically functions) serve the same purpose but differ in how they fail. Failure to include a file results in a warning; failure to require a file results in a fatal error. Because the configuration and MySQL files are critical to the site's functionality, failure to incorporate them should be fatal. Conversely, failure to incorporate the header or footer is just a cosmetic issue, not that you'd want that to happen either.

You may notice that I did not use require_once or include_once. These two control structures run checks to ensure that the same file isn't incorporated multiple times by the same script. Because of those repeated checks, using them has an adverse effect on the site's performance. In this site, which is straightforward, a repeated inclusion of a file is highly unlikely, so it's best to go with the more direct require and include. If you have a very complex site, with lots of included files that include other files, using the _once variants may be necessary. You will see a couple of appropriate uses of include_once in later chapters.

## 4 USER ACCOUNTS

The next step in the evolution of the Knowledge is Power e-commerce site is to create a system of user accounts. When the site is complete, PayPal will be the crucial part in the registration process, but just to understand the user account system on its own, as well as to be able to create an administrative user for the next chapter, let's look at user accounts as a separate entity first.

There are four primary facets to the implementation of user accounts in this chapter. First, a new user registers. Second, a registered user logs in. Third, the logged-in user logs out (in theory, many people, including me, don't always do so). Fourth, users need to be able to retrieve a forgotten password and change an existing password.

Although this example won't be storing any sensitive e-commerce data, security will still be taken seriously, for the benefit of the customers and the site itself. In a few places, I'll make recommendations as to how you can increase security even further, and the chapter ends with even more suggestions.

### DEFINING HELPER FUNCTIONS

Before getting into the primary scripts, there are three helper functions that you should define. The first will greatly facilitate handling some of the site's forms. The second will transform a user-supplied password into a format that's more secure to store. And the third will redirect the browser should the user not meet the requirements for accessing a particular page.

There are a few benefits to using these custom functions:

- Keeps complex logic from cluttering up other code
- Allows the same logic to be used in multiple scripts
- Makes changes to the logic a snap

The last two are really the key points: If you separate out processes, they can be used by different parts of a site without having to repeat the code. And if you later decide you need to tweak the process, you can do so in one place.

### Creating Form Inputs

The functionality provided by the scripts in this chapter is almost entirely form-based: The user must complete a registration, login, change password, or forgot password form. All these forms use just two types of form inputs — text and password (not counting the submit buttons). An input starts off with this simple HTML:

```html
<input type="type" name="name" id="name" />
```

For example:

```html
<input type="text" name="username" id="username" />
```

In cases where the form was submitted but not properly completed, the user will be presented with the form again. As a convenience, the form should remember the entered values (that is, it should be sticky). To achieve that effect, you need to add value="whatever value" to each input. In PHP code, that would be:

```html
<input type="text" name="username" id="username" value="<?php echo $_POST['username']; ?>" />
```

However, the first time the form is loaded, $_POST['username'] won't be set, so the code should really be:

```html
<input type="text" name="username" id="username" value="<?php if (isset($_POST['username'])) echo $_POST['username']; ?>" />
```

You can add sizes to the inputs, if you want. I chose not to size them, so they would all be equally sized to the browser's default.
