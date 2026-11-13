# # "Homework" Solution

Here's the solution to the "homework" challenge posed above. These changes were required to insert a "Delete this Joke" link next to each joke:

+   - Previously, we passed an $addjoke variable with our "Add a Joke!" link at the bottom of the page to signal that our script should display the joke entry form, instead of the usual list of jokes. In a similar fashion, we pass a $deletejoke variable with our "Delete this Joke" link to indicate our desire to have a joke deleted.

+   - For each joke, we fetch the ID column from the database, along with the Joketext column, so that we know which ID is associated with each joke in the database.

+   - We set the value of the $deletejoke variable to the ID of the joke that we're deleting. To do this, we insert the ID value fetched from the database into the HTML code for the "Delete this Joke" link of each joke.

+   - Using an if statement, we watch to see if $deletejoke is set to a particular value (through the isset function) when the page loads. If it is, we use the value to which it is set (the ID of the joke to be deleted) in an SQL DELETE statement that deletes the joke in question.

Here's the complete code, which is also available as challenge.php in the code archive (located at http://www.sitepoint.com/books/). If you have any questions, don't hesitate to post them in the SitePoint.com forums!

```
<html>
<head>
<title> The Internet Joke Database </title>
</head>
<body>
<?php
if (isset($addjoke)): // The user wants to add a joke
?>
<form action="<?=$PHP_SELF?>" method="post">
<p>Type your joke here:<br />
<textarea name="joketext" rows="10" cols="40" wrap>
</textarea><br />
<input type="submit" name="submitjoke" value="SUBMIT" />
</p>
</form>
<?php
else:
    // Connect to the database server
```