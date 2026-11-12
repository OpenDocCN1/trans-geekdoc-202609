```
</tr>";
foreach ($authors as $author) {
 echo "<tr>";
 echo "<td>{$author['author_id']}</td>";
 echo "<td>{$author['last_name']}</td>";
 echo "<td>{$author['first_name']}</td>";
 echo "<td>{$author['email']}</td>";
 echo "<td>{$author['biography']}</td>";
 echo "<td><a href='form_edit_author.php?author_id={$author['author_id']}'>
Edit</a></td>";
 echo "</tr>";
}
echo "</table">;
} else {
 echo "No author found.";
}
?>
</body>
</html>
```

These modifications addition a "Edit" column to the author display table, where each line contains a "Edit" link pointing to a script named "form_edit_author.php" with the corresponding author ID passed as a