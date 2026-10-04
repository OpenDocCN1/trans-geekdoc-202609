# Chapter 6

![](bbox=[0.057, 0.087, 0.843, 0.563])

# How It Works

The commit.php code is very much the same as what you saw already, but there is an interesting twist in movie.php. Let's look at it in some detail.

First, look at what the start of the script. We defined a switch on a query string parameter action. If the action is edit, we query the database for a record corresponding to the id specified in the id query string parameter and set some variables. These variables are set to void if action is not edit.

```
switch($_GET['action']) {
    case "edit":
        $movies = "SELECT
            FROM
                'movie'
            WHERE
                'movie'.movie_id = ''.$_GET['id'].'\n            *";
        $result = mysql_query($movies)
        or die("Invalid query: " . mysql_error());
        $row = mysql_fetch_array($result , MYSQL_ASSOC );
```

188