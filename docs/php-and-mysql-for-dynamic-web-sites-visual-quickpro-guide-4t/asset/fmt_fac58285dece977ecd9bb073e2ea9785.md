
This email address validation pattern is pretty good, although not perfect. It will allow some invalid addresses to pass through (like ones starting with a period or containing multiple periods together). However, a 100 percent foolproof validation pattern is ridiculously long, and frequently using regular expressions is really a matter of trying to exclude the bulk of invalid entries without inadvertently excluding any valid ones.

---

### Tip

Regular expressions, particularly PCRE ones, can be extremely complex. When starting out, it’s just as likely that your use of them will break the validation routines instead of improving them. That’s why practicing like this is important.

---

### Finding All Matches

Going back to the PHP functions used with Perl-Compatible regular expressions, `preg_match()` has been used just to see if a pattern matches a value or not. But the script hasn’t been reporting what, exactly, in the value did match the pattern. You can find out this information by providing a variable as a third argument to the function:

```
preg_match(pattern, subject, $match);
```

The `$match` variable will contain the first match found (because this function only returns the first match in a value). To find every match, use `preg_match_all()`. Its syntax is the same:

```
preg_match_all(pattern, subject, $matches);
```

This function will return the number of matches made, or FALSE if none were found. It will also assign to `$matches` every match made. Let’s update the PHP script to print the returned matches, and then run a couple more tests.

#### To report all matches

**1.** Open `pcre.php` ([Script 14.1](#ch14.html#ch14ex01)) in your text editor or IDE, if it is not already.

**2.** Change the invocation of `preg_match()` to (**[Script 14.2](#ch14.html#ch14ex02)**):

```
if (preg_match_all ($pattern, $subject, $matches) ) {
```

There are two changes here. First, the actual function being called is different. Second, the third argument is provided a variable name that will be assigned every match.

**Script 14.2.** To reveal exactly what values in a string match which patterns, this revised version of the script will print out each match. You can retrieve the matches by naming a variable as the third argument in `preg_match()` or `preg_match_all()`.

---

```
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
2       1.0 Transitional//EN" "http://www.w3.org/
3       TR/xhtml1/DTD/xhtml1-transitional.dtd">
4   <html xmlns="http://www.w3.org/1999/
5       xhtml" xml:lang="en" lang="en">
6   <head>
7       <meta http-equiv="Content-Type"
8           content="text/html; charset=utf-8" />
9       <title>Testing PCRE</title>
10  </head>
11  <body>
12  <?php // Script 14.2 - matches.php
13  // This script takes a submitted string
14      and checks it against a submitted pattern.
15  // This version prints every match made.
16
17  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
18
19      // Trim the strings:
20      $pattern = trim($_POST['pattern']);
21      $subject = trim($_POST['subject']);
22
23      // Print a caption:
24      echo "<p>The result of checking<br />
25          <b>$pattern</b><br />against<br />
26          $subject<br />is ";
27
28      // Test:
29      if (preg_match_all ($pattern,
30          $subject, $matches) ) {
31          echo 'TRUE!</p>';
32
33          // Print the matches:
34          echo '<pre>' . print_r($matches,
35              1) . '</pre>';
36
37      } else {
38          echo 'FALSE!</p>';
39      }
40
41  } // End of submission IF.
42  // Display the HTML form.
43  ?>
44  <form action="matches.php"
45      method="post">
46      <p>Regular Expression Pattern:
47          <input type="text" name="pattern"
48          value="<?php if (isset($pattern)) echo
49          htmlentities($pattern); ?>" size="40" />
50          (include the delimiters)</p>
51      <p>Test Subject: <textarea
52          name="subject" rows="5"
53          cols="40"><?php if (isset($subject))
54          echo htmlentities($subject); ?>
55          </textarea></p>
56      <input type="submit" name="submit"
57          value="Test!" />
58  </form>
59  </body>
60  </html>
```

---

**3.** After printing the value *TRUE*, print the contents of `$matches`:

```
echo '<pre>' . print_r($matches, 1) . '</pre>';
```

Using `print_r()` to output the contents of the variable is the easiest way to know what’s in `$matches` (you could use a `foreach` loop instead). As you’ll see when you run this script, this variable will be an array whose first element is an array of matches made.

**4.** Change the form’s `action` attribute to *matches.php*:

```
<form action="matches.php" method="post">
```

This script will be renamed, so the `action` attribute must be changed, too.

**5.** Change the subject input to be a textarea:

```
<p>Test Subject: <textarea name="subject" rows="5" cols="40"> <?php if (isset($subject)) echo htmlentities($subject); ?></textarea></p>
```

---

In order to be able to enter in more text for the subject, this element will become a textarea.

**6.** Save the file as `matches.php`, place it in your Web directory, and test it in your Web browser.

For the first test, use **for** as the pattern and *This is a formulaic test for informal matches*. as the subject ![Image](graphics/circle-a.jpg). It may not be proper English, but it’s a good test subject.

![Image](graphics/14_figure_17_a.jpg)

![Image](graphics/circle-a.jpg)This first test returns three matches, as the literal text *for* was found three times.

For the second test, change the pattern to **for.\*** ![Image](graphics/circle-b.jpg). The result may surprise you, the cause of which is discussed in the sidebar, “[Being Less Greedy](#ch14.html#ch14sb02).” To make this search less greedy, the pattern could be changed to **for.\*?**, whose results would be the same as those in ![Image](graphics/graycircle-a.jpg).

![Image](graphics/14_figure_18_b.jpg)

![Image](graphics/circle-b.jpg)Because regular expressions are “greedy” by default (see the sidebar), this pattern only finds one match in the string. That match happens to start with the first instance of *for* and continues until the end of the string.

For the third test, use **for\[\S\]\***, or, more simply **for\S\*** ![Image](graphics/circle-c.jpg). This has the effect of making the match stop as soon as a white space character is found (because the pattern wants to match *for* followed by any number of non–white space characters).

---

### Being Less Greedy

A key component to Perl-Compatible regular expressions is the concept of *greediness*. By default, PCRE will attempt to match as much as possible. For example, the pattern `<.+>` matches any HTML tag. When tested on a string like *<a href=”page.php”>Link</a>*, it will actually match that entire string, from the opening `<` to the closing one. This string contains three possible matches, though: the entire string, the opening tag (from *<a* to *">*), and the closing tag (*</a>*).

To overrule greediness, make the match *lazy*. A lazy match will contain as little data as possible. Any quantifier can be made lazy by following it with the question mark. For example, the pattern `<.+?>` would return two matches in the preceding string: the opening tag and the closing tag. It would not return the whole string as a match. (This is one of the confusing aspects of the regular expression syntax: the same character—here, the question mark—can have different meanings depending on its context.)

Another way to make patterns less greedy is to use negative classes. The pattern `<[^>]+>` matches everything between the opening and closing `<>` except for a closing `>`. So using this pattern would have the same result as using `<.+?>`. This pattern would also match strings that contain newline characters, which the period excludes.
