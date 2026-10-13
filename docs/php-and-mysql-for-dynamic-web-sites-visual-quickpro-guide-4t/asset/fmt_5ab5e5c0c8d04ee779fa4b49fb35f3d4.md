
It’s possible, albeit unlikely, that `$_SESSION['lid']` does not equate to a record from the `words` table. In that case the query would return no records (but run without error). Consequently, the default language words must now be retrieved. Notice that neither this block of code, nor that in Step 5, actually fetches the returned record. That will happen, for both potential queries, in Step 7.

### 7. Fetch the retrieved words into an array, free the resources, and close the PHP section:

```php
$words = mysqli_fetch_array($r, MYSQLI_ASSOC);

mysqli_free_result($r);

?>
```

After this point, the `$words` array represents all of the navigation and common elements in the user’s selected language (or the default language).

Calling `mysqli_free_result()` isn’t necessary, but makes for tidy programming.

### 8. Start the HTML page:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title><?php echo $words['title']; ?></title>
```

Note that the encoding is also indicated in a `META` tag, even though the PHP `header()` call already identifies the encoding. This is just a matter of being thorough.

The header file as written uses as the title of every page a value in the `$words` array (i.e., the page title will always be the same for every page in a chosen language). You could easily modify this code so that the page’s title is a combination of the language word and a page-specific variable, such as `$page_title` used in [Chapter 3](#ch03.html#ch03) and subsequent examples.

### 9. Add the CSS:

```css
<style type="text/css" media="screen">
body { background-color: #ffffff; }
.content {
  background-color: #f5f5f5;
  padding-top: 10px; padding-right: 10px; padding-bottom: 10px; padding-left: 10px;
  margin-top: 10px; margin-right: 10px; margin-bottom: 10px; margin-left: 10px;
}
  a.navlink:link { color: #003366; text-decoration: none; }
  a.navlink:visited { color: #003366; text-decoration: none; }
  a.navlink:hover { color: #cccccc; text-decoration: none; }
  .title {
    font-size: 24px; font-weight: normal; color: #ffffff;
    margin-top: 5px; margin-bottom: 5px; margin-left: 20px;
    padding-top: 5px; padding-bottom: 5px; padding-left: 20px;
  }
</style>
```

This is all taken from a template I found somewhere some time ago. It adds a little decoration to the site.

### 10. Complete the HTML head and begin the page:

```html
</head>
<body>
<table width="90%" border="0" cellspacing="10" cellpadding="0" align="center">
<tr>
  <td colspan="2" bgcolor= "#003366" align="center"> <p class="title"><?php echo $words['title']; ?></p></td>
</tr>
<tr>
  <td valign="top" nowrap= "nowrap" width="10%"><b>
```

The page itself uses a table for the layout, with one row showing the page title, the next row containing the navigation links on the left and the page-specific content on the right, and the final row containing the copyright ![Image](graphics/circle-d.jpg). You’ll see in this code that the page title will also be language-specific.

![Image](graphics/17_figure_16_d.jpg)

![Image](graphics/circle-d.jpg)The page layout showing the rows and columns of the main HTML table.

### 11. Start displaying the links:

```php
<?php
echo '<a href="index.php" class="navlink">' . $words['home'] . '</a><br />
<a href="forum.php" class="navlink">' . $words['forum_home'] . '</a><br />';
```

The first two links will always appear, whether the user is logged in or not, and regardless of the page they’re currently viewing. For each link, the text of the link itself will be language-specific.

### 12. If the user is logged in, show “new thread” and logout links:

```php
if (isset($_SESSION['user_id'])) {
  if (basename($_SERVER['PHP_SELF']) == 'forum.php') {
    echo '<a href="post.php" class="navlink">' . $words['new_thread'] . '</a><br />';
  }
  echo '<a href="logout.php" class="navlink">' . $words['logout'] . '</a><br />';
```

Confirmation of the user’s logged-in status is achieved by checking for the presence of a `$_SESSION['user_id']` variable. If it’s set, then the logout link can be created. Before that, a check is made to see if this is the `forum.php` page. If so, then a link to start a new thread is created (users can only create new threads if they’re on the forum page; you wouldn’t want them to create a new thread on some of the other pages, like the home page, because it wouldn’t be clear to which forum the thread should be posted). The code for checking what page it is, using the `basename()` function, was first introduced in [Chapter 12](#ch12.html#ch12), “[Cookies and Sessions](#ch12.html#ch12).”

### 13. Display the links for users not logged in:

```php
} else {
  echo '<a href="register.php" class="navlink">' . $words['register'] . '</a><br />
  <a href="login.php" class= "navlink">' . $words['login'] . '</a><br />';
}
```

If the user isn’t logged in, links are provided for registering and logging in.

### 14. Start a form for choosing a language:

```php
echo '</b><p><form action="forum.php" method="get">
<select name="lid">
<option value="0">' . $words['language'] . '</option>
';
```

The user can choose a language (which is also a forum), via a pull-down menu ![Image](graphics/circle-e.jpg). The first value in the menu will be the word “language,” in the user’s default language. The select menu’s `name` is *lid*, short for *language ID*, and its `action` attribute points to `forum.php`. When the user submits this simple form, they’ll be taken to the forum of their choice.

![Image](graphics/17_figure_17_e.jpg)

![Image](graphics/circle-e.jpg)The language pull-down menu, with each option in its native language.

### 15. Retrieve every language from the database, and add each to the menu:

```php
$q = "SELECT lang_id, lang FROM languages ORDER BY lang_eng ASC";
$r = mysqli_query($dbc, $q);
if (mysqli_num_rows($r) > 0) {
  while ($menu_row = mysqli_fetch_array($r, MYSQLI_NUM)) {
    echo "<option value=\"$menu_row[0]\">$menu_row[1] </option>\n";
  }
}
mysqli_free_result($r);
```

This query retrieves the languages and the language ID from the `languages` table. Each is added as an option to the select menu.

Again, calling `mysqli_free_result()` isn’t required, but doing so can help limit bugs and improve performance. In particular, when you have pages that run multiple `SELECT` queries, `mysqli_free_result()` can help avoid confusion issues between PHP and MySQL.

### 16. Complete the form and the PHP page:

```php
echo '</select><br />
<input name="submit" type="submit" value="' . $words['submit'] . '" />
</form></p>
    </td>
    <td valign="top" class="content">';
?>
```

### 17. Save the file as `header.html`.

Even though it contains a fair amount of PHP, this script will still use the `.html` extension (which I prefer to use for template files). Make sure that the file is saved using UTF-8 encoding.

### 18. Create a new document in your text editor or IDE, to be named `footer.html` ([Script 17.2](#ch17.html#ch17ex02)):

```html
<!-- Script 17.2 - footer.html -->
```

### 19. Complete the HTML page:

```html
    </td>
  </tr>
  <tr>
    <td colspan="2" align="center">&copy; 2011 Larry Ullman</td>
  </tr>
</table>
</body>
</html>
```

### 20. Save the file as `footer.html`.

Again, make sure that the file is saved using UTF-8 encoding.

### 21. Place both files in your Web directory, within a folder named `includes`.

**Script 17.2.** The footer file completes the HTML page.

---

1   `<!-- Script 17.2 - footer.html -->`
2     `</td>`
3      `</tr>`
4
5      `<tr>`
6      `<td colspan="2" align="center">&copy;`
