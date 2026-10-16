# 25. ADDING RESERVATION FEATURES

# Modify Homepage Based On Access Privileges

We need to modify the homepage to show various information based on who is logged in. There are three different contexts for viewing information on the homepage:

+   1. When no one is logged in.
+   2. When a user is logged in with “admin” privileges.
+   3. When a user is logged in with “user” privileges.

When no one is logged in, we only want to display the movies as in Figure 25.10. When a user with admin privileges is logged in, we want the trashcan icon to be displayed for removing a movie (See Figure 25.11). Finally, when logged in with user privileges, the shopping cart icon can be displayed for adding the movie to a cart. The cart only shows if copies are available to reserve and the user has not already reserved it as in Figure 25.12.

![](bbox=[0.5, 0.28, 0.87, 0.47])

![](bbox=[0.11, 0.49, 0.48, 0.68])

![](bbox=[0.5, 0.49, 0.87, 0.68])

> The shopping cart icon is the Font Awesome fa-shopping-cart icon which is free to use.
> The shopping cart link takes the user to a new page we create for reserving that movie.