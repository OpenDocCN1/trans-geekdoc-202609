# Chapter 18: String Matching with Regular Expressions

To all matches for a regular expression within a string, use the `preg_match_all()` function. `preg_match_all()` takes the same parameters as `preg_match()`:

+   - The regular expression

+   - The string to search through

+   - An array to hold the matches (note that for `preg_match_all()` the array is not optional)

+   - Optional flags for the match operation

+   - An optional offset to start the search from

As with `preg_match()`, `preg_match_all()` returns the number of matches as an integer. Unlike `preg_match()`, where this value can only be 0 or 1, `preg_match_all()` returns the total number of matches in the string:

```
$text = "Call Mary on 499 012 3456, John on 876 543 2101, or Karen:\n777 111 2345";
echo preg_match_all("/\w+\s(\d{3})\s(\d{4})", $text, $matches); //
Displays "3"
```

`preg_match_all()` stores all matches in the array passed to it as the third argument. The matches are stored in the first element of the array (with an index 0) as a nested array:

```
$scores = "John: 143 points, Anna: 175 points, and Nicole: 119 points";
preg_match_all("/(\w+):\s(\d+)"/, $scores, $matches);
echo $matches[0][0] . " <br />"; // Displays "John: 143 points"
echo $matches[0][1] . " <br />"; // Displays "Anna: 175 points"
echo $matches[0][2] . " <br />"; // Displays "Nicole: 119 points"
```

If your expression contains subpatterns, the matches are stored in subsequent array elements. Consider the following example:

```
// The following code displays:
$John scored 143
$Anna scored 175
$Nicole scored 119
```

```
echo $matches[1][0] . " " . $matches[2][0] . " <br />";
echo $matches[1][1] . " " . $matches[2][1] . " <br />";
echo $matches[1][2] . " " . $matches[2][2] . " <br />";
```

As you can see from this example, the first element is a nested array containing all the matches from the first subpattern (the players' names), and the second contains 2 matches from the second subpattern (the scores). For each subpattern in the expression, an extra element is created in the matches array.