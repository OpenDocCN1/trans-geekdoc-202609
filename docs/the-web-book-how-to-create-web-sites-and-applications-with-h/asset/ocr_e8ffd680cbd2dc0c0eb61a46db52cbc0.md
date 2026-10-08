```
{ echo "Sorry, no matches found."; }
```

```
if ($total > 0)
{



while ($row = mysql_fetch_array($q))
{
echo $row["firstname"] . " " . $row["surname"] . "<br>";
} # while

} # if matches found

} # else
```

```
# End the page properly
echo "</body>";
echo "</HTML>";
```

```
exit();
```

```
function sanitize_form_text($t)
{
$t = strip_tags($t);
$t = ereg_replace("[^A-Za-z0-9@._-]", "", $t);
return $t;
}

?>
```

If you've been reading through this book in sequence, then hopefully you'll be able to understand most of the above. Here are some points to help you.

+   - The program displays one of two web pages. The first time around, it displays the search form which, when submitted, launches the same php program again. The form contains a textbox called searchtext, and a pair of radio buttons called searchtype with possible values of FULL or PARTIAL. If the searchtype has been set (to either PARTIAL or to FULL) at the start of the program, this indicates that the form has been submitted, so, rather than displaying the form again, we do the actual search instead.
- I've created a function called sanitize_form_text, which is listed at the bottom of the program. At the point where the value of the search text is retrieved from the form, it then gets sanitized.