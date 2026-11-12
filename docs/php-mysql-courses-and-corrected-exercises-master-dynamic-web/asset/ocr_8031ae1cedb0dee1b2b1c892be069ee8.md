```
}
echo "</table>";
} else {
    echo "No author found.";
}
?>
</body>
</html>
```

Part 2 of this code first checks if there are authors in the database by checking if the number of authors retrieved from the $authors variable is greater than zero with the if (count($authors) > 0) condition. If authors are found, the code generates an HTML table to display the details of each author. Otherwise, if no authors are found, it displays the message "No authors found."

Within the foreach loop, each author in the $authors array is browsed. For each author, the code generates a new table row with author details such as author ID ($author['author_id']), last name ($author['last_name']), first name ($author['first_name']), email ($author['email']), and biography ($author[biography]). These details are displayed in table cells (<td>) and each author is displayed in a new table row (<tr>).

Running display_authors.php produces a result similar to the following: