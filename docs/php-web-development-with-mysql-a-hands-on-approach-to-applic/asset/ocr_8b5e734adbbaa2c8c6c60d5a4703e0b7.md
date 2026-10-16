# 24. ADDING A NAVIGATION MENU

Listing 24.4.

```
1. <nav ...>
2. <!-- ... -->
3. <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
4.   <div class="navbar-nav">
5.     <a class="nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>"
6.        href="<?= dirname($_SERVER['PHP_SELF']) ?>">Home </a>
7.     <?php if (!isset($_SESSION['user_name'])): ?>
8.       <a class="nav-item nav-link<?= $page_title == MR_LOGIN_PAGE ? ' active' : '' ?>"
9.          href="login.php">Login</a>
10.    <?php endif; ?>
11.  </div>
12. </div>
13. </nav>
```

Let’s break this down on its own:

```
<?php if (!isset($_SESSION['user_name'])): ?>
<a class="nav-item nav-link<?= $page_title == MR_LOGIN_PAGE ? ' active' : '' ?>" href="login.php">Login</a>
<?php endif; ?>
```

We have two conditions here. The outer condition checks to see if the user is not logged in. If you recall from login.php three session variables get set when a user gets logged in:

```
$_SESSION['user_id'] = $row['id'];
$_SESSION['user_name'] = $row['user_name'];
$_SESSION['user_access_privileges'] = $row['access_privileges'];
```

If the user is already logged in, there is no need to show a link to the “Login” page. Assuming the user is not logged in, we display a link to the “Login” page and then evaluate the ternary condition. It—similar to the link for the home page—evaluates whether the user is currently on the “Login” page or not.