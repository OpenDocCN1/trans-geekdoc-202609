
**Script 12.10.** The `header.html` file now also references `$_SESSION` instead of `$_COOKIE`.

---

```html
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
       1.0 Strict//EN" "http://www.w3.org/TR/
       xhtml1/DTD/xhtml1-strict.dtd">
2   <html xmlns="http://www.w3.org/1999/xhtml">
3   <head">
4       <title><?php echo $page_title; ?>
           </title>
5       <link rel="stylesheet" href="includes/
           style.css" type="text/css"
           media="screen" />
6       <meta http-equiv="content-type"
           content="text/html; charset=utf-8" />
7   </head>
8   <body>
9       <div id="header">
10          <h1>Your Website</h1>
11          <h2>catchy slogan...</h2>
12      </div>
13      <div id="navigation">
14          <ul>
15              <li><a href="index.php">Home
                   Page</a></li>
16              <li><a href="register.php">
                   Register</a></li>
17              <li><a href="view_users.php">
                   View Users</a></li>
18              <li><a href="password.php">
                   Change Password</a></li>
19              <li><?php // Create a login/
                   logout link:
20      if (isset($_SESSION['user_id'])) {
21          echo '<a href="logout.php">Logout</a>';
22      } else {
23          echo '<a href="login.php">Login</a>';
24      }
25      ?></li>
26          </ul>
27      </div>
28      <div id="content"><!-- Start of the
           page-specific content. -->
29  <!-- Script 12.10 - header.html -->
```

---

**Script 12.11.** Destroying a session, as you would in a logout page, requires special syntax to delete the session cookie and the session data on the server, as well as to clear out the `$_SESSION` array.

---

```php
1   <?php # Script 12.11 - logout.php #2
2   // This page lets the user logout.
3   // This version uses sessions.
4
5   session_start( ); // Access the
       existing session.
6
7   // If no session variable exists,
       redirect the user:
8   if (!isset($_SESSION['user_id'])) {
9
10      // Need the functions:
11      require ('includes/login_functions.
           inc.php');
12      redirect_user( );
13
14  } else { // Cancel the session:
15
16      $_SESSION = array( ); // Clear the
           variables.
17      session_destroy( ); // Destroy the
           session itself.
18      setcookie ('PHPSESSID', '', time( )-3600,
           '/', '', 0, 0); // Destroy the cookie.
19
20  }
21
22  // Set the page title and include the
       HTML header:
23  $page_title = 'Logged Out!';
24  include ('includes/header.html');
25
26  // Print a customized message:
27  echo "<h1>Logged Out!</h1>
28  <p>You are now logged out!</p>";
29
30  include ('includes/footer.html');
31  ?>
```

---

### Deleting session variables

When using sessions, you ought to create a method of deleting the session data. In the current example, this would be necessary when the user logs out.

Whereas a cookie system only requires that another cookie be sent to destroy the existing cookie, sessions are slightly more demanding, since there are both the cookie on the client and the data on the server to consider.

To delete an individual session variable, you can use the `unset()` function (which works with any variable in PHP):

```php
unset($_SESSION['var']);
```

But to delete every session variable, you shouldn’t use `unset()`, instead, reset the `$_SESSION` array:

```php
$_SESSION = array();
```

Finally, to remove all of the session data from the server, call `session_destroy()`:

```php
session_destroy();
```

Note that prior to using any of these methods, the page must begin with `session_start()` so that the existing session is accessed. Let’s update the `logout.php` script to clean out the session data.

### To delete a session

**1.** Open `logout.php` ([Script 12.6](#ch12.html#ch12ex06)) in your text editor or IDE.

**2.** Immediately after the opening PHP line, start the session (**[Script 12.11](#ch12.html#ch12ex11)**):

```php
session_start();
```

Anytime you are using sessions, you must call the `session_start()` function, preferably at the very beginning of a page. This is true even if you are deleting a session.

**3.** Change the conditional so that it checks for the presence of a session variable:

```php
if (!isset($_SESSION['user_id'])) {
```

As with the `logout.php` script in the cookie examples, if the user is not currently logged in, they will be redirected.

**4.** Replace the `setcookie()` lines (that delete the cookies) with:

```php
$_SESSION = array();
session_destroy();
setcookie ('PHPSESSID', '', time() - 3600, '/', '', 0, 0);
```

The first line here will reset the entire `$_SESSION` variable as a new array, erasing its existing values. The second line removes the data from the server, and the third sends a cookie to delete the existing session cookie in the browser.

---

### Garbage Collection

Garbage collection with respect to sessions is the process of the server automatically deleting the session files (where the actual data is stored). Creating a logout system that destroys a session is ideal, but there’s no guarantee all users will formally log out as they should. For this reason, PHP includes a cleanup process.

Whenever the `session_start()` function is called, PHP’s garbage collection kicks in, checking the last modification date of each session (a session is modified whenever variables are set or retrieved). Two settings dictate garbage collection: `session.gc_maxlifetime` and `session.gc_probability`. The first states after how many seconds of inactivity a session is considered idle and will therefore be deleted. The second setting determines the probability that garbage collection is performed, on a scale of 1 to 100. With the default settings, each call to `session_start()` has a 1 percent chance of invoking garbage collection. If PHP does start the cleanup, any sessions that have not been used in more than 1,440 seconds will be deleted.

You can change these settings using the `ini_set()` function, although be careful in doing so. Too frequent or too probable garbage collection can bog down the server and inadvertently end the sessions of slower users.

---

**5.** Remove the reference to `$_COOKIE` in the message:

```php
echo "<h1>Logged Out!</h1>
<p>You are now logged out!</p>";
```

Unlike when using the cookie version of the `logout.php` script, you cannot refer to the user by their first name anymore, as all of that data has been deleted.

**6.** Save the file as `logout.php`, place it in your Web directory, and test it in your browser ![Image](graphics/circle-e.jpg).

![Image](graphics/12_figure_21_e.jpg)

![Image](graphics/circle-e.jpg) The logout page (now featuring sessions).

---

> **Tip**
>
> The `header.html` file only needs to check if `$_SESSION['user_id']` is set, and not if the page is the logout page, because by the time the header file is included by `logout.php`, all of the session data will have already been destroyed. The destruction of session data applies immediately, unlike with cookies.

---

> **Tip**
>
> Never set `$_SESSION` equal to `NULL` and never use `unset($_SESSION)`. Either could cause problems on some servers.

---

> **Tip**
>
> In case it’s not absolutely clear what’s going on, there exists three kinds of information with a session: the session identifier (which is stored in a cookie by default), the session data (which is stored in a text file on the server), and the `$_SESSION` array (which is how a script accesses the session data in the text file). Just deleting the cookie doesn’t remove the data file and vice versa. Clearing out the `$_SESSION` array would erase the data from the text file, but the file itself would still exist, as would the cookie. The three steps outlined in this logout script effectively remove all traces of the session.
