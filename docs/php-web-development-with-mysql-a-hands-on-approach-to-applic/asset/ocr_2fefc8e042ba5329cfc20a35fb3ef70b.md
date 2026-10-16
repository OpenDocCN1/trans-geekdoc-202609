# 20. BASIC HTTP AUTHENTICATION

Currently, our *MovieListing* application has no protection from someone simply deleting all of our movies in our database or adding movie entries that we might not approve of.

In this chapter, we implement basic HTTP authentication that adds a level of protection for features of our application we do not want to expose to everyone.

In a follow-on chapter covering Security, I will discuss authentication and authorization further. Basic HTTP Authentication is a simple way to control who can use particular web pages.

The question is, what features do we want to require authentication for? Given that our application allows anyone to access the whole website, we need to add basic authentication to any feature that modifies or deletes data from the application. This limits who can change the database to trusted users who know a valid username and password combination. Therefore we will require authentication to:

+   - `addmovie.php`
+   - `removemovie.php`
+   - `editmovie.php`

# Password Protection with HTTP Authentication

Users should be able to add a movie by clicking on the link shown in Figure 20.1, remove a movie (Figure 20.2), or edit movie details via the link in Figure 20.3. Before carrying out any of these operations, we want to display the authorization dialog shown in Figure 20.4, or something similar, to verify their identity. The exact dialog you see varies depending on your browser and operating system.

![](bbox=[0.36, 0.48, 0.87, 0.61])

![](bbox=[0.36, 0.62, 0.87, 0.71])

![](bbox=[0.36, 0.72, 0.87, 0.86])