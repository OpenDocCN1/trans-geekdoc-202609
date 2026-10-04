# Chapter 7

The date validation is as simple to understand, if you know about regular expressions. Here's a quick look at it:

```
$movie_release = trim($_POST['movie_release']);
if (!preg_match('/([0-9]{2})-([0-9]{2})-([0-9]{4})/', $movie_release, $releasepart) ||
empty($movie_release)) {
    $Error = "Please+enter-a+date+with-dd-mm-yyyy+format%21%0D%0A";
} else {
    $movie_release = mktime(0, 0, 0, $releasepart['2'], $releasepart['1'], $releasepart['3']);
    if ($movie_release == '') {
        $Error = "Please+enter-a+date+with-dd-mm-yyyy+format%21%0D%0A";
    }
}
```

As you can see in this first use the `trim()` function to clear all leading and trailing spaces in the received string to make sure our user enters something other than just a space.

> The string manipulation functions are found at the PHP Web site at www.php.net/strings. You can find them other very useful functions there.

The next statement contains two tests for a regular expression match. The regular expression is '/([0-9]{2})-([0-9]{2})-([0-9]{4})/. What does this do? [0-9]{2} specifies that we want to check for numbers between 0 and 9 with two occurrences. For example 02 matches but not 2. The same logic applies to the [0-9]{4} statement: The only difference is that we are expecting four digits in our number. These four digits are the year part of the date.

So, in English, it means: I want to start with a number with two digits, followed by a hyphen (-), and another group of two digits, and a hyphen (-), and finish with a four-digit number.

```
if (!preg_match('/([0-9]{2})-([0-9]{2})-([0-9]{4})/', $movie_release, $releasepart) ||
empty($movie_release)) { }
```

Now, this is not exactly what our regular expression says. It says that if it matches our we will split it into three chunks, each chunk delimited by the parentheses.

This cutting is performed by the `preg` function. If the $movie_release string matches the pattern, preg will cut the string into parts and store each part as an element of the $releasepart array in our example.

Be sure to read the PHP manual about regular expressions at www.php.net/regex and consult a few tutorials to learn the power of using regular expressions. (A starting tutorial can be found at www.phpbuilder.com/columns/dario19990616.php3)

If our date was 02-03-2003, the array would be as follows:

+   * [0] => 02-03-2003
* [1] => 02