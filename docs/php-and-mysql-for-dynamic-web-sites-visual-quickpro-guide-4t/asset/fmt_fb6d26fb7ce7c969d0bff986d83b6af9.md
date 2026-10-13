
A unique index is placed on the `email` field, and another index is placed on the combination of the `email` and `pass` fields. These two fields will be used together during the login query, so indexing them as one, creating an index called `login`, makes sense.

---

### Creating the Home Page

The home page for the site, called `index.php`, will be a model for the other pages on the public side. It will require the configuration file (for error management) and the header and footer files to create the HTML design. This page will also welcome the user by name, assuming the user is logged in.

![Image](graphics/18_figure_10_a.jpg)

If the user is logged in, the index page will greet them by name.

#### To write index.php

**1.** Begin a new PHP document in your text editor or IDE, to be named `index.php` (**[Script 18.5](#ch18.html#ch18ex05)**):

```php
<?php # Script 18.5 - index.php
```

**2.** Include the configuration file, set the page title, and include the HTML header:

```php
require ('includes/config.inc.php');

$page_title = 'Welcome to this Site!';

include ('includes/header.html');
```

The script includes the configuration file first so that everything that happens afterward will be handled using the error-management processes established therein. Then the `header.html` file is included, which will start output buffering, begin the session, and create the initial part of the HTML layout.

**Script 18.5.** The script for the site's home page, which will greet a logged-in user by name.

---

```php
1   <?php # Script 18.5 - index.php
2   // This is the main page for the site.
3
4   // Include the configuration file:
5   require ('includes/config.inc.php');
6
7   // Set the page title and include the
8       HTML header:
9   $page_title = 'Welcome to this Site!';
10  include ('includes/header.html');
11
12  // Welcome the user (by name if they are
13      logged in):
14  echo '<h1>Welcome';
15  if (isset($_SESSION['first_name'])) {
16      echo ", {$_SESSION['first_name']}";
17  }
18  echo '!</h1>';
19  ?>
20  <p>Spam spam spam spam spam spam
21  spam spam spam spam spam spam
22  spam spam spam spam spam spam
23  spam spam spam spam spam spam.</p>
24  <p>Spam spam spam spam spam spam
25  spam spam spam spam spam spam
26  spam spam spam spam spam spam
27  spam spam spam spam spam spam.</p>
28
29  <?php include ('includes/footer.html'); ?>
```

**3.** Greet the user and complete the PHP code:

```php
echo '<h1>Welcome';

if (isset($_SESSION['first_name'])) {
    echo ", {$_SESSION['first_name']}";
}

echo '!</h1>';
?>
```

The *Welcome* message will be printed to all users. If a `$_SESSION['first_name']` variable is set, the user's first name will also be printed. So the end result will be either just *Welcome!* or *Welcome, <Your Name>!*.

![Image](graphics/18_figure_11_b.jpg)

If the user is not logged in, this is the home page they will see.

**4.** Create the content for the page:

```html
<p>Spam spam...</p>
```

You might want to consider putting something more useful on the home page of a real site. Just a suggestion....

**5.** Include the HTML footer:

```php
<?php include ('includes/footer.html'); ?>
```

The footer file will complete the HTML layout (primarily the menu bar on the right side of the page) and conclude the output buffering.

**6.** Save the file as `index.php`, place it in your Web directory, and test it in a Web browser.

### Registration

The registration script was first started in [Chapter 9](#ch09.html#ch09). It has since been improved upon in many ways. This version of `register.php` will do the following:

*   Both display and handle the form
*   Validate the submitted data using regular expressions and the Filter extension
*   Redisplay the form with the values remembered if a problem occurs (the form will be *sticky*)
*   Process the submitted data using the `mysqli_real_escape_string()` function for security
*   Ensure a unique email address
*   Send an email containing an activation link (users will have to activate their account prior to logging in—see the "[Activation Process](#ch18.html#ch18sb03)" sidebar)

#### To write register.php

**1.** Begin a new PHP document in your text editor or IDE, to be named `register.php` (**[Script 18.6](#ch18.html#ch18ex06)**):

```php
<?php # Script 18.6 - register.php
```

**2.** Include the configuration file and the HTML header:

```php
require ('includes/config.inc.php');
$page_title = 'Register';
include ('includes/header.html');
```

**Script 18.6.** The registration script uses regular expressions for security and a sticky form for user convenience. It sends an email to the user upon a successful registration.

---

```php
1   <?php # Script 18.6 - register.php
2   // This is the registration page for the
3       site.
4   require ('includes/config.inc.php');
5   $page_title = 'Register';
6   include ('includes/header.html');
7
8   if ($_SERVER['REQUEST_METHOD'] == 'POST') {
9       // Handle the form.
10
11      // Need the database connection:
12      require (MYSQL);
13
14      // Trim all the incoming data:
15      $trimmed = array_map('trim', $_POST);
16
17      // Assume invalid values:
18      $fn = $ln = $e = $p = FALSE;
19
20      // Check for a first name:
21      if (preg_match('/^[A-Z \'.-]{2,20}$/i', $trimmed['first_name'])) {
22          $fn = mysqli_real_escape_string($dbc, $trimmed['first_name']);
23      } else {
24          echo '<p class="error">Please enter your first name!</p>';
25      }
26
27      // Check for a last name:
28      if (preg_match('/^[A-Z \'.-]{2,40}$/i', $trimmed['last_name'])) {
29          $ln = mysqli_real_escape_string($dbc, $trimmed['last_name']);
30      } else {
31          echo '<p class="error">Please enter your last name!</p>';
32      }
33
34      // Check for an email address:
35      if (filter_var($trimmed['email'], FILTER_VALIDATE_EMAIL)) {
36          $e = mysqli_real_escape_string($dbc, $trimmed['email']);
37      } else {
38          echo '<p class="error">Please enter a valid email address!</p>';
39      }
40
41      // Check for a password and match against the confirmed password:
42      if (preg_match('/^\w{4,20}$/', $trimmed['password1'])) {
43          if ($trimmed['password1'] == $trimmed['password2']) {
44              $p = mysqli_real_escape_string($dbc, $trimmed['password1']);
45          } else {
46              echo '<p class="error">Your password did not match the confirmed password!</p>';
47          }
48      } else {
49          echo '<p class="error">Please enter a valid password!</p>';
50      }
51
52      if ($fn && $ln && $e && $p) { // If everything's OK...
53
54          // Make sure the email address is available:
55          $q = "SELECT user_id FROM users WHERE email='$e'";
56          $r = mysqli_query($dbc, $q) or trigger_error("Query: $q\n<br />MySQL Error: " . mysqli_error($dbc));
57
58          if (mysqli_num_rows($r) == 0) { // Available.
59
60              // Create the activation code:
61              $a = md5(uniqid(rand(), true));
62
62              // Add the user to the database:
63              $q = "INSERT INTO users (email, pass, first_name, last_name, active, registration_date) VALUES ('$e', SHA1('$p'), '$fn', '$ln', '$a', NOW())";
64              $r = mysqli_query($dbc, $q) or trigger_error("Query: $q\n<br />MySQL Error: " . mysqli_error($dbc));
```
