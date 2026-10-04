# Using Tables to Display Data

```
$movie_leadactor = $row['movie_leadactor'];

//get director's name from people table
get_director($movie_director);

// get lead actor's name from people table
get_leadactor($movie_leadactor);

$movie_details <<<<EOD
<tr>
<td>$movie_name</td>
<td>$director</td>
<td>$leadactor</td>
</tr>
EOD
}

$movie_details .= <<<EOD
<tr>
<td>Total :$num_movies Movies</td>
</tr>
EOD;
$movie_footer = "</table>";

$movie =<<MOVIE
$movie_header
$movie_details
$movie_footer
Movie;

print "There are $num_movies movies in our database";
print "$movie";
?
```

2. Save your file and reload it in your browser. Your screen should now look like that in Figure 4-4.

# How It Works

With the functions get_director and get_leadactor added, the script requests specific information be requested from the server for each row in the table. This enables you to pull the information you want without muddling up your original query. You cleaned up the formatting of the last two rows with the change in the end of the script.

Congratulations! You have successfully developed a powerful script that will query a database and put its contents into an HTML table. Give yourself a pat on the back. But like all good explorers, onward we must go.