# 24. ADDING A NAVIGATION MENU

This chapter adds a navigation bar (otherwise known as a “navbar”) to the top of our *Movie Reservations* application. A navbar makes it much more user-friendly to navigate around the application. With a few exceptions, we want our navbar to display on all the pages in our application. Additionally, we want our navbar to be context-sensitive. That is, it should indicate or hint what page we are on and display links we have access to based on our privileges. When we first navigate to the Home page, without being logged in, this is what we want our navbar to look like Figure 24.1.

![](bbox=[0.48, 0.1, 0.85, 0.3])

# Create Navbar Logic

Since almost every page in our application will be displaying a navbar, we will create a script to be included by these pages. Create a script called navmenu.php and add this PHP code at the very top that checks the $page_title variable of the page that included this script:

```
```php
<?php
    $page_title = isset($page_title) ? $page_title : "";
?>
```
```

> > *It is crucial that the opening PHP tag <?php is the first thing in your file (no spaces preceding) as this code runs before HTML headers are sent.*

Remember we set the variable $page_title to one of the definitions created in pagetitles.php in the scripts that include navmenu.php (e.g. index.php, login.php, etc.).

Since we are using session variables in our application and navmenu.php will be included by most every script, let's add the following code after the $page_title check that starts or resumes our session:

```
```php
<?php
    $page_title = isset($page_title) ? $page_title : "";

    if (session_status() == PHP_SESSION_NONE)
    {
        session_start();
    }
?>
```
```