command to go back into "normal HTML mode", the above example should make perfect sense.

There's an alternate form of the if-else statement that can make your code more readable in situations like this. Here's the outline for a multi-purpose page using the alternate if-else form:

```
<html>
<head>
<title> Multi-Purpose Page Outline </title>
</head>
<body>

<?php if (condition): ?>

<!--- HTML content to display if condition is true -->

<?php else: ?>

<!--- HTML content to display if condition is false -->

<?php endif; ?>

</body>
</html>
```

Okay, now that we have all the tools we need in hand, let's look at a sample page of our site (samplepage.php in the code archive located at http://www.sitepoint.com/books/):

```
<html>
<head>
<title> Sample Page </title>
</head>
<body>

<?php if ( !isset($name) ): ?>

<!--- No name has been provided, so we
prompt the user for one. -->

<form action="<?=echo($PHP_SELF)?>" method="get">
Please enter your name: <input type="text" name="name"
/>
<input type="submit" value="GO" />
</form>

<?php else: ?>

<p>Your name: <?=$name?></p>

<p>This paragraph contains a <a
href="newpage.php?name=<?=urlencode($name)?>">link</a>
that passes the name variable on to the next
```