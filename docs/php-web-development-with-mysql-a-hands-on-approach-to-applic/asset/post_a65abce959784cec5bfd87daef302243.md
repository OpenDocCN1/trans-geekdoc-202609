
## 24. ADDING A NAVIGATION MENU

The <nav> element has these Bootstrap class attributes set for the following purpose:

| Class Property | Purpose |
|---|---|
| .navbar | Specifies this is a navbar |
| .sticky-top | Sticks to the top as the page scrolls |
| .navbar-expand-md | For responsive collapsing |
| .navbar-dark | For white text on dark color backgrounds |

Also, notice I set the style attribute to a background-color. If you omit this, you will have white text on a black background for the menu.

Next is a standard <a href> link with the class attribute set to navbar-brand with the href set to the home folder location, along with an image icon referencing MR_HOME_PAGE, which must be defined in pagetitles.php. Create a folder under the Movie Listing folder called resources to store your image icons. I called this one movie_rental_icon.png.

> *The movie projector icon is free to use with Creative Commons attribution, which I found here¹¹.*

Before we forget, let's define MR_HOME_PAGE. Open pagetitles.php and add the following MR_HOME_PAGE definition right before the MR_SIGNUP_PAGE definition:

```php
<?php
// Page Titles
define('MR_HOME_PAGE', 'Movie Reservations');
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
```

Getting back to navmenu.php, we then have a <button> element with a class attribute set to navbar-toggler for the button to collapse for responsive design. This class collapses the navigation menu on mobile devices under a hamburger icon as in Figure 24.2

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_380_0.png)

[1] here: https://iconfinder.com/icons/753134/festival_film_icon

### Create Navbar Logic

Then we have a <div> tag with a class set to collapse navbar-collapse to group and hide/ collapse menu items. In this <div>, we put navbar-nav item links to our home, login, and signup pages. In fact, we already have a navigation link to our Home page here. Let's take a closer look at it in Listing 24.2.

### Listing 24.2.

```
<nav ...>
<!-- ... -->
<div class="collapse navbar-collapse" id="navbarNavAltMarkup">
<div class="navbar-nav">
<a class="nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>" 
href="<?= dirname($_SERVER['PHP_SELF']) ?>">Home </a>
</div>
</div>
</nav>
```

To create a navigation item, you need to create a child <div> tag container with the class attribute set to navbar-nav. Next, you create a child <a href> link with the class set to nav-item nav-link. However, you will notice I added some PHP code with a ternary operator before the href attribute. This link is for the home page. However, we want the navigation link for the current page we are on to be highlighted (e.g., active):

```
"nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>"
```

If the home page is being displayed (i.e. index.php) the class attribute will be set as:

```
class="nav-item nav-link active"
```

Otherwise, it is set as:

```
class="nav-item nav-link"
```

We use this mechanism for all pages that include navmenu.php and have a link to its page.

For more details, see the documentation on how Bootstrap's Navbar[2] works.

[2] Bootstrap's Navbar: https://getbootstrap.com/docs/4.0/components/navbar/

### Add the Navigation Bar

Now that we have our navmenu.php script, let’s make some modifications to index.php and include the navmenu.php script. Open the index.php script and add the following PHP code to the very top of the script, before the <!DOCTYPE html> element:

```
<?php
require_once('pagetitles.php');
$page_title = MR_HOME_PAGE;
?>
<!DOCTYPE html>
<html>
```

This properly sets our $page_title variable for use in navmenu.php which we include from pagetitles.php and changes our page title from “Movies I Like” to “Movie Reservations”. Next, in the <head> element, modify the <title> element with this code:

```
<html>
  <head>
    <link >
    <title><?= $page_title ?></title>
  </head>
  <body>
```

This changes our <title> element from Movies I Like to Movie Reservations. Next, right below the <body> element, include the navmenu.php script:

```
<body>
<?php
  require_once('navmenu.php');
?>
  <div class="card">
    <div class="card-body">
```

Next, inside the <div class="card-body"> element, modify the <h1> element to reference the $page_title instead of Movies I Like:

```
<div class="card">
  <div class="card-body">
    <h1><?= $page_title ?></h1>
```

> *Later, when we add more of the reservation system features, we will remove the link to add a movie (since it will be in the navigation menu). We also hide the trash can icon unless a user is logged in with admin privileges.*

### Add Navigation Bar to Details Page

When users select a movie, they are taken to the “Movie Details” page for that movie. The user either needs to press the back button in the browser or select the Movies I Like link to get back to the home page. It would be better to include the navbar and remove the extra link for a consistent user experience throughout the application. We want our “Movie Details” page to look like Figure 24.3.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_383_0.png)

Notice that the “Home” menu item is not active because we are on the “Movie Details” page instead of the home page. Open pagetitles.php and add the following MR_DETAILS_PAGE definition right after the MR_HOME_PAGE definition:

```
<?php
// Page Titles
define('MR_HOME_PAGE', 'Movie Reservations');
define('MR_DETAILS_PAGE', 'Movie Reservations - Details');
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
```

Open the moviedetails.php script and add the following PHP code to the very top of the script, before the <!DOCTYPE html> element:

```
<?php
require_once('pagetitles.php');
$page_title = MR_DETAILS_PAGE;
?>
<!DOCTYPE html>
<html>
```

## 24. ADDING A NAVIGATION MENU

This code properly sets our $page_title variable for use in navmenu.php, which we include from pagetitles.php.

Next, in the <head> element, modify the <title> element with this code:

```
<html>
<head>
<link ...>
<title><?= $page_title ?></title>
...
</head>
<body>
```

Next, right below the <body> element, include the navmenu.php script:

```
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
```

Next, inside the <div class="card-body"> element, remove the <nav class="nav"> link to the index.php page and replace it with <h1>Movie Details</h1> and a horizontal line (<hr/>) as in Listing 24.3.

### Listing 24.3.

```
1. Unchanged Lines
2. <div class="card">
3. <div class="card-body">
4. - Removed Lines
5. - <nav class="nav">
6. - <a class="nav-link" href="index.php">Movies I Like</a>
7. - </nav>
8. + Added Lines
9. + <h1>Movie Details</h1>
10. + <hr/>
```

> When we start to add more of the reservation system features, we will hide the link to edit a movie unless a user is logged in with admin privileges.

### Add Login Link to Navigation Bar

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_385_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_385_1.png)

We need to add a nav link item to the login.php page and have login.php include navmenu.php. When we are on the home page and not logged in, we want our nav menu to look like Figure 24.4.

Notice that the Login link is not active, indicating we are not on the login.php page. When we navigate to the Login page, we want our nav menu to look like Figure 24.5

Notice now that the Login link is active, indicating we are on the login.php page.

Open up the login.php script and include the navmenu.php script right after the <body> element:

```
<body>
<?php
  require_once('navmenu.php');
?>
<div class="card">
  <div class="card-body">
```

Now open the navmenu.php script. We will add a child <a href> link with the class set to nav-item nav-link for our Login page right below the link to the Home page. Add the code in Listing 24.4, and I will explain it below.
