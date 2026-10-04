# Building Databases

Next, we are creating a multidimensional array. That's fancy talk for an array with more than one index. This one is two-dimensional. Think of a two-dimensional array as being a spreadsheet, and it is difficult to understand.

```
if (mysql_num_rows($result) > 0) {
    while ($row = mysql_fetch_assoc($result)) {
        $p[$row['id']][] = $row['power'];
    }
}
```

The trick here is that we have multiple powers for the same id. By adding to the $sp array, a new item is created for each power that has the same id. The end result is that we have a array of characters, each element of which contains a p[x] array of powers. This is a multidimensional array.

Now we go back through our temporary array $sp, and pull out each character it holds. The $key variable contains the character id, and $value the array of characters. We implement the powers into, comma-separated list of powers, and store that in the $powers array, using the character id ($key) as index. We end up with an array that contains a list of powers for each character.

```
foreach ($sp as $key => $value) {
    $p[$key] = implode('*', $value);
}
```

Oh no, another JOIN. This is similar to the M.N query, with a couple of exceptions. First of all, we are linking the character table twice. You can see that we are creating two instances of table, one c for "character" and one n for "nemesis". This distinction is very important.

```
sql = "SELECT c.id, n.alias FROM char_main c JOIN char_good_bad_link
JOIN char_main n ON (c.id = gb_good_id AND n.id = gb_bad_id)
OR (n.id = gb_good_id AND c.id = gb_bad_id)";
```

The other exception is the ON clause. We have stated we are attempting to link to other characters as "enemies". They can be opponents, or nemesis, whatever. Typically, you expect good evil and vice-versa. However, we are allowing any character to be the enemy of any other character. This makes more interesting because we are using a table with a bad-id and a good-id. If you have two characters that are enemies, which gets stored in the good_id column

The answer is it doesn't matter. What we want to do is make sure that we don't have any duplicates in the char_good_bad_link table, but also that we don't reverse duplicate. In other words, if you have a row with good_id=3 and bad_id=7, then good_id=7 and bad_id=3 must be considered a duplicate. There is no way to prevent that in MySQL using primary keys, so we must take care of that in query. We do that in a couple of places.

In this instance, we are two queries in one. The first one gets all instances of character where the character's id is in the good_id field and IDs are in the bad_id field. The part of the ON reverses that, and pulls all instances of each character where the character's ID is in the bad_id field and its enemies' ids are in the good_id field. This does not prevent reverse duplicate (that is handled elsewhere), but it makes sure we get every possible link to a character's enemy.