count($cats), the number of elements in the $cats array. If $cats doesn't contain any elements (i.e. if no categories were selected), then $i will start out equal to count($cats), and the contents of the loop won't be executed at all!

This all seems very slick, but there's actually a better way. Instead of using the count function, we can simply keep going until we reach a value of $i for which $cat[$i] is empty. When we do, we know we'll have reached the end of the list of category IDs:

```
```php
$i = 0; // First index
while ($cats[$i] != "") { // while we're not at the end
// process $cats[$i]
$i = $i + 1;
}
```
```

This will run a little quicker because we don't call a function each time through the loop. Plus it's a teeny bit cleverer, and we programmers have to have our fun when we can! Believe it or not, however, PHP spoils our fun by having a completely separate type of loop that's specialized for looping through arrays, called a foreach loop. Here's what the code looks like in this case:

```
```php
foreach ($cats as $catID) {
// Process $catID
}
```
```

This will execute the code inside the loop once for each item in the $cats array (you see where the foreach loop gets its name), and will assign the item for each loop to the variable $catID. Since this code is indisputably tidier than the equivalent while loop, we'll settle on this as a solution. All that remains is to determine what to do for each selected category ID.

Well, before we became sidetracked by all these different types of loops, we were about to take our array of category IDs and use it to place our newly-inserted joke into its corresponding categories. A cursory examination of our database layout reveals that we just have to insert an entry into the JokeLookup table for each category of which that joke should be a member. Recall that each entry in the JokeLookup table consists of a joke ID (JID) and a category ID (CID), which together indicate that a particular joke belongs to a particular category. Here's the finished foreach loop:

```
```php
foreach ($cats as $catID) {
$sql = "INSERT IGNORE INTO JokeLookup
SET JID=$jid, CID=$catID";
$ok = @mysql_query($sql);
if ($ok) {
$numCats = $numCats + 1;
} else {
echo("<p>Error inserting joke into category ".
" $catID: " . mysql_error() . "</p>");
}
```
```