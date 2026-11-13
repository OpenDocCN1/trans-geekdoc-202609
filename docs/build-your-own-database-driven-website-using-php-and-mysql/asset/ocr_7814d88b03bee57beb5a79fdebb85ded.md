value of the JokeDate column to be inserted into the database. MySQL actually has dozens of these functions, but we'll only introduce them as required. For a complete function reference, refer to Appendix B.

We now have the code that will allow a user to type a joke and add it to our database. All that remains is to slot it into our existing joke viewing page in a useful fashion. Since most users will only want to view our jokes, we don't want to mar our page with a big, ugly form unless the user expresses an interest in adding a new joke. For this reason, our application is well suited for implementation as a multi-purpose page. Here's the code (available as jokes.php in the code archive located at http://www.sitepoint.com/books/):

```
<html>
<head>
<title> The Internet Joke Database </title>
</head>
<body>
<?php
if (isset($addjoke)): // If the user wants to add a joke ?>
<form action="<?=$PHP_SELF?>" method="post">
<p>Type your joke here:<br />
<textarea name="joketext" rows="10" cols="40" wrap>
</textarea><br />
<input type="submit" name="submitjoke" value="SUBMIT" />
</p>
</form>
<?php
else: // Default page display
// Connect to the database server
$dbcnx = @mysql_connect("localhost", "root",
"mypasswd");
if (!$dbcnx) {
echo( "<p>Unable to connect to the " .
"database server at this time.</p>" );
exit();
}
// select the jokes database
if (! @mysql_select_db("jokes") ) {
echo( "<p>Unable to locate the joke " .
"database at this time.</p>" );
exit();
}
// If a joke has been submitted,
// add it to the database.
if ($submitjoke == "SUBMIT") {
```