```
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s
</td></tr>',
htmlspecialchars($row->id),
htmlspecialchars($row->quote),
htmlspecialchars($row->author),
htmlspecialchars($row->year)
);
}
sqlite_close($db);
} else {
printf('<tr><td colspan="4">Connection failed:
%s</td></tr>',
htmlspecialchars($error));
}
?>
</table>
```

*Retrieving Data from SQLite (sqlite_fetch.php: excerpt)*

**TIP:** Using sqlite_fetch_all() reads the whole result set into memory simultaneously. if you are using ext/sqlite: ext/sqlite3 does not support this feature. So, if you do not have much data, this is the best-performing method. If you have more data, an iterative approach using sqlite_fetch_array() and sqlite_fetch_object() might be better.

# Using Prepared Statements with SQLite

```
$stmt = $db->prepare('INSERT INTO quotes (quote, author, year) VALUES (:quote, :author, :year)');
$stmt->bindParam(':quote', ...);
```