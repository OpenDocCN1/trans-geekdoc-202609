# #40: Rearranging a Table

Let’s look at several utilities that use regular expressions. For a more complex example, let’s say that you have a bunch of entries in an HTML table that looks like this:

```
<tr><td>last_name, first_name</td>
<td>address</td>
<td>phone number</td>
</tr>
```

Now assume that your boss just can’t leave well enough alone and insists that you change it to this format:

```
<tr><td>first_name</td>
<td>last_name</td>
<td>address</td>
<td>phone number</td>
</tr>
```

You can do this in one fell swoop with backreferencing:

```
$table = preg_replace('/<td>([^<]*)\s*<([^<]*)<\/td>/',
   '<td>$1<<td>', " \n" . '<td>$2<<td>',
   $table);
```

A bit of explanation is necessary. I split the arguments into three lines because they’re easier to read that way. Notice that there are two groupings, and before the second (the last name), there is a \s* to match any excess whitespace. Finally, notice how the replacement is a concatenation. That’s because we want a newline, but \n represents a newline only in double-quoted strings. Otherwise, you want to use single-quoted strings, or else you may need to add a bunch of backslashes in your backreferences.

Now just make sure to tell your boss that this task took you forever, so that you still have time to play video games while pretending to work.

# #41: Creating a Screen Scraper

A screen scraper program accesses a web page and picks through the HTML for interesting or useful data. Here’s a very simple one that extracts all hyperlinks from a page and then categorizes them. This scraper includes a lot of regular expressions, so let’s take it one step at a time. First, let’s check that the input (in $_REQUEST["page"]) is actually a hyperlink and not someone trying to monkey around with files on the local system:

```
<?php
$page = $_REQUEST["page"];
if (!preg_match(\'|^https{0,1}://|\', $page)) {
   print "URL $page invalid or unsupported.";
   exit;
}
```