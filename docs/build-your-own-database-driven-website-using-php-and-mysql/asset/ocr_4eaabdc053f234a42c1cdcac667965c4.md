```
// select the page we want
$joketext=$textarray[$page];

// Bold and italics
$joketext = eregi_replace("\\[b\]", "<b>", $joketext);
$joketext = eregi_replace("\\[eb\]", " </b>", $joketext);
$joketext = eregi_replace("\\[i\]", "<i>", $joketext);
$joketext = eregi_replace("\\[ei\]", " </i>", $joketext);

// Paragraphs and line breaks
$joketext = eregi_replace("\\r", "", $joketext);
$joketext = eregi_replace("\\n\\n", "</p><p>", $joketext);
$joketext = eregi_replace("\\n", "<br />", $joketext);

// Hyperlinks
$joketext = ereg_replace(
  "\\[L=([-_.-/a-zA-Z0-9!&%#?,'=~:+]+)\\[EL]",
  "<a href="\\1">\\1</a>", $joketext);
$joketext = ereg_replace(
  "\\[L=([-_.-/a-zA-Z0-9!&%#?,'=~:+]+)".
  "([-_.-/a-zA-Z0-9 !&%#?,'=~:+]+)\\[EL]",
  "<a href="\\1">\\2</a>", $joketext);

if ($page != 0) {
  $prevpage = $page - 1;
  echo("<p><a href="$PHP_SELF?id=$id&page=$prevpage".
    "Previous Page</a></p>");
}

echo( "<p>$joketext</p> " );

if ($page < count($textarray) - 1) {
  $nextpage = $page + 1;
  echo("<p><a href="$PHP_SELF?id=$id&page=$nextpage".
    "Next Page</a></p>");
}
...
```

Don't forget to provide documentation so that users of your joke submission form know what tags are available and what each of them does.

# Automatic Content Submission

It seems a shame to have spent so much time and effort on a content management system that's so easy that anyone can use it, if the only people who are actually allowed to use it are the site administrators. Furthermore, while it's extremely convenient for an administrator not to have to edit HTML to make updates to the site's content, he or she must still transcribe submitted documents into the "Add New Joke" form, and convert any formatted text