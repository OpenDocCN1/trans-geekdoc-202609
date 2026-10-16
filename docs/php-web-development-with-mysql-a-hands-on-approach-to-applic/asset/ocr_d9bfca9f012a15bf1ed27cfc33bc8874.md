# 15. DISPLAYING A LIST OF ITEM DETAILS

# Storing Database Connection Definitions

Next, let's create a separate file called dbconnection.php (Listing 15.2) for our database credentials that we will create constants for. Since we'll need these values in multiple scripts, we store them in a file we can require or include across our application.

# Listing 15.2.

```
```php
1. <?php
2.   /* dbconnection.php */
3.
4.   // Database connection constants
5.   define('DB_HOST', 'localhost');
6.   define('DB_USER', 'movieguru');
7.   define('DB_PASSWORD', 'ilikemovies');
8.   define('DB_NAME', 'Movie');
```
```

> Typically, you would use an environment variable to hold sensitive information, but for these examples, this is sufficient.

# Displaying a Movie Listings Table

Now let's create our main Movie Listing script and call it index.php. Starting right after our opening <body> tag, we display our heading “Movies I Like”. Next, let's switch back to our index.php page and add a couple of nested <div> tags right below our opening <body> tag to display our movies in What Bootstrap calls a “card” as shown in Listing 15.3.

# Listing 15.3.

```
```html
1. <body>
2.   <div class="card">
3.     <div class="card-body">
4.     </div>
5.   </div>
6.   <script ...
7.   ...
8. </body>
9. </html>
```
```

Within the inner most <div> tag, add an <h1> heading called “Movies I Like”:

```
```html
<body>
  <div class="card">
    <div class="card-body">
      <h1>Movies I Like</h1>
```
```