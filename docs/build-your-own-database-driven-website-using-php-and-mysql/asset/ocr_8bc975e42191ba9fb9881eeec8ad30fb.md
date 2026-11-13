```
// Display the text of each joke in a paragraph
// with a "Delete this Joke" link next to each.
while ( $row = mysql_fetch_array($result) ) {
    $jokeid = $row["ID"];
    $joketext = $row["JokeText"];
    echo("<p>$joketext .
        "<a href='$PHP_SELF?deletejoke=$jokeid'>" .
        "Delete this Joke</a></p>");
}

// when clicked, this link will load this page
// with the joke submission form displayed.
echo("<p><a href='$PHP_SELF?addjoke=1'>Add a " .
    "Joke!</a></p>");

endif;

?>
</body>
</html>
```