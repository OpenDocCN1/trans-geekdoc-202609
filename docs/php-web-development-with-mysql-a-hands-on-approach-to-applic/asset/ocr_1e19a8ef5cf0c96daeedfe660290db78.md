# Link to the “Add a Movie” Page from the Listing Page

Now that our “Add a Movie” page is complete, let’s add a link to the addmovie.php script from the main “Movies I Like” index.php script. (Figure 16.7).

Add the link to the addmovie.php script in the <body> element, right below the “Movies I Like” title index.php script:

```
<body>
<div class="card">
    <div class="card-body">
        <h1>Movies I Like</h1>
        <p>If you have a movie you would like to include, feel free to
            <a href='addmovie.php'> add one</a></p>
```

![](bbox=[0.45, 0.15, 0.85, 0.34])

# Exercises

+   1. Create an “Add Movie” page with a form that allows users to insert a movie in the database.
+      1. Ensure users submit a title, rating, director, running time, and genre.
+      2. Put an “Add Movie” button on the movie listings page.
+   2. Add at least one new genre of movies to the form. Ensure the data is saved to the database. Display the value (if selected) on the details page.
+   3. Add a field for the year the movie was released to the form. Allow years from 1900 to ten years in the future. Ensure the data is saved to the database. Display the year released on the details page.