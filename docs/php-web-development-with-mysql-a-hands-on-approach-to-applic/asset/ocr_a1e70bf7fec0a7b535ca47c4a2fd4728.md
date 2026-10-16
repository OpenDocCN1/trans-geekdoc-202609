# 17. REMOVING DATA USING THE WEB APPLICATION

Reload the updated index.php script in a browser. Now, when we hover our cursor over a trashcan icon of one of the movie listings, we see that our destination hyperlink is the remove movie.php script. The hyperlink includes a query parameter of id_to_delete set to the primary key of the movie we are interested in deleting. See Figure 17.2.

The browser sends this query parameter, and PHP parses that into the $_GET[] superglobal array.

# Creating a “Remove a Movie Page”

Any page dedicated to removing data from our application should clearly display what we want to delete. Doing so allows users to confirm if they want to delete this information or not. For example, when we select a movie we want to delete, our browser should take us to a page that looks like Figure 17.3.

Although it is not necessary, I like putting important text and actions—like selecting the “Delete Movie” submit button—in <span style="color:red">red</span>. Bootstrap also has button-specific classes we could use to differentiate it.

# Initial Page Layout

Create another PHP script and call it remove movie.php. Again, start with a simple boilerplate that includes the necessary Bootstrap framework components and call the page title: “Remove a Movie.” Next, add a couple of nested <div> tags right below our opening <body> tag to display our movies in a Bootstrap card as shown in Listing 17.2.

![](bbox=[0.55, 0.05, 0.95, 0.4])

![](bbox=[0.55, 0.4, 0.95, 0.75])