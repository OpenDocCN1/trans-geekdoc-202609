# Chapter 3

```
echo "<table border='1\n";
while ($rows=mysql_fetch_assoc($results)) {
    echo "<tr>\n";
    foreach($rows as $value) {
        echo "<td>\n";
        echo $value;
        echo "</td>\n";
    }
    echo "</tr><br>\n";
}
echo "</table>\n";n
?>
```

# How It Works

You should see the same result as in the previous example. As you can see, we simply listed all the fields we wanted to, regardless of the table they were in. (MySQL will find them as long as the tableName is referenced somewhere) We did this in the first line of the SELECT statement:

```
SELECT movie_name, movietype_label
```

Then we use MySQL what we wanted to access and what type of join should be used to join them in these statements:

```
FROM movie
LEFT JOIN movietype
```

We used the most common LEFT join statement in this case. Although there are other things that go along with this, the LEFT in layman's terms means that the second table (movietype in our example) is dependent on the first table (movie). We are getting the main information from movie, and “looking up” a bit of information from movietype.

We tell the server which field to use to join them together in this line:

```
ON movie_type = movietype_id
```

Again, we don't need to clarify which table is being used, but if you have overlapping fieldnames across tables, you can add this if you like, to avoid confusion.

We keep our condition above only showing the movies that were made after 1990, and sorted by numerical movie year with these lines:

```
WHERE movie.movie_year>1990
ORDER BY movie_type";
```

And the rest of the code is the same. See, joining wasn't that bad, was it?