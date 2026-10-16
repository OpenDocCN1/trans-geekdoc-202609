# 18. EDITING DATA USING THE WEB APPLICATION

# First Steps

First, we will display the “Edit a Movie” title in an <h1> tag set within the <body> element:

```
<body>
    <div class="card">
        <div class="card-body">
            <h1>Edit a Movie</h1>
```

Next, let’s create a link back to the index.php page if the user does not want to update this movie and a horizontal line (<hr/> element):

```
<body>
<div class="card">
    <div class="card-body">
        <h1>Edit a Movie</h1>
        <nav class="nav">
            <a class="nav-link" href="index.php">Movies I Like</a>
        </nav>
        <hr/>
```

As in the previous “Remove a Movie” page, we will need to access the database for the movie we want to edit, so we need to include our dbconnection.php script and connect to our Movie database as shown in Listing 18.1.

# Listing 18.1.

```
1. <body>
2.     <div class="card">
3.         <div class="card-body">
4.             <h1>Edit a Movie</h1>
5.         <p><a class='nav-link' href='index.php'>Movies I Like</a></p>
6.     <hr/>
7.         <?php
8.             require_once('dbconnection.php');
9. 
10.            $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
11.                or trigger_error(
12.                    'Error connecting to MySQL server for' . DB_NAME,
13.                    E_USER_ERROR
14.                );
```