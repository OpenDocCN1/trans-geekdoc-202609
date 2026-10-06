# Part III: Using PHP in Practice

You can even sort by more than one column by separating the column names with:

```
mysql> SELECT favoriteGenre, firstName, lastName FROM members ORDER BY
favoriteGenre, firstName;
+------------------------------------------------+
| favoriteGenre | firstName | lastName |
+------------------------------------------------+
| crime | Jane | Field |
| crime | John | Sparks |
| horror | Marty | Pareene |
| thriller | Mary | Newton |
| romance | Jo | Scrivener |
| scifi | Nick | Blakeley |
| nonFiction | Bill | Swan |
+------------------------------------------------+
7 rows in set (0.00 sec)
```

You can read this ORDER BY clause as: "Sort the results by favoriteGenre, then by firstName." Notice how the results are ordered by genre, but where the genre is "crime", the results are sorted by firstName "Jane" "John".

By default, MySQL sorts columns in ascending order. If you want to sort in descending order, add the keyword DESC after a field name. To avoid ambiguity, you can also add ASC after a field name to explicitly sort in order:

```
mysql> SELECT favoriteGenre, firstName, lastName FROM members ORDER BY
favoriteGenre DESC, firstName ASC;
+------------------------------------------------+
| favoriteGenre | firstName | lastName |
+------------------------------------------------+
| nonFiction | Bill | Swan |
| scifi | Nick | Blakeley |
| romance | Jo | Scrivener |
| thriller | Mary | Newton |
| horror | Marty | Pareene |
| crime | Jane | Field |
| crime | John | Sparks |
+------------------------------------------------+
7 rows in set (0.00 sec)
```

Remember that ORDER works faster on a column that has an index, because indexes are already sorted in order.

# Using Pattern Matching for Flexible Queries

So far, all the WHERE clauses you've looked at have been fairly precise:

```
SELECT * from fruit WHERE name = 'banana';
SELECT * from fruit WHERE id >= 2;
```

374