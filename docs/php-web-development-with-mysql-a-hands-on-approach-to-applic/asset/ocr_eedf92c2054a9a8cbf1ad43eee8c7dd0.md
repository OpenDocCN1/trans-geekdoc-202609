# Add Logout Link to Navigation Bar

Let’s add a nav link item for users to log out. Also, let’s display the user name when a user is logged in to the navigation menu. When we are on the homepage and logged in, we want our nav menu to look like Figure 24.6.

Open up the navmenu.php script. Add a child <a href> link with the class set to nav-item nav-link for our “Logout” page right below the link to the “Login” page. Add the code in Listing 24.5 on lines 9–10, and I will explain it below.

![](bbox=[0.52, 0.15, 0.86, 0.36])

# Listing 24.5.

```
```php
1. <nav ...>
2.   ...
3.   <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
4.     <div class="navbar-nav">
5.       <a class="nav-item nav-link...">Home </a>
6.       <?php if (!isset($_SESSION['user_name'])): ?>
7.       <a class="nav-item nav-link...">Login</a>
8.       <?php else: ?>
9.       <a class='nav-item nav-link'
10.      href='logout.php'>Logout (<?= $_SESSION['user_name'] ?>)</a>
11.      <?php endif; ?>
12.    </div>
13.  </div>
14. </nav>
```
```

Again, let’s look at this on its own:

```
```php
<?php else: ?>
<a class='nav-item nav-link'
  href='logout.php'>Logout (<?= $_SESSION['user_name'] ?>)</a>
<?php endif; ?>
```
```

We’ll add an else clause after the if check (line 8 previous listing) to handle logged-in users. We display a link to the logout.php script and display the user’s name (held in $_SESSION['user_name']).