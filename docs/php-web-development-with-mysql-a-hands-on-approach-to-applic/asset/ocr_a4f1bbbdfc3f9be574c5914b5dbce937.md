# 24. ADDING A NAVIGATION MENU

If the user is not logged in OR the user is logged in but doesn’t have admin privileges, the link to the “Add a Movie” page will not be displayed. Assuming the user is logged in AND has admin privileges, we show a link to the “Add a Movie” page and then evaluate the ternary condition, which evaluates whether or not the “Add a Movie” page is active.

# Add Navigation Bar to Unauthorizedaccess.php

Since it is plausible for someone to navigate to a page they do not have access to, let’s add the navbar to the unauthorizedaccess.php script. Our page will look like Figure 24.12.

Open up the unauthorizedaccess.php script and include the navmenu.php script right after the <body> element:

```
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
```

![](bbox=[0.5, 0.35, 0.87, 0.48])

# Add Navigation Bar to editmovie.php

Let’s add the navbar to the editmovie.php script. We want our menu to look like Figure 24.13.

> > You will need to log in as a user with access_privileges set to admin to test this.

![](bbox=[0.5, 0.54, 0.87, 0.73])

Open pagetitles.php and add the following MR_EDIT_MOVIE_PAGE definition right after the MR_ADD_MOVIE_PAGE definition:

```
<?php
// Page Titles
// ...
define('MR_ADD_MOVIE_PAGE', 'Movie Reservations - Add Movie');
define('MR_EDIT_MOVIE_PAGE', 'Movie Reservations - Edit Movie');
```