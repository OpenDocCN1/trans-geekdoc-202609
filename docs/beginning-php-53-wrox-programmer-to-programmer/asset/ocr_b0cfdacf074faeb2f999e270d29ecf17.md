# Appendix A: Solutions to Exercises

```
[pubYear] => 1859
[authorName] => Dickens
)
```

```
[3] => Array
[title] => Paradise Lost
[authorId] => 4
[pubYear] => 1667
[authorName] => Milton
)
```

```
[4] => Array
[title] => Animal Farm
[authorId] => 5
[pubYear] => 1945
[authorName] => Orwell
)
```

```
[5] => Array
[title] => The Trial
[authorId] => 1
[pubYear] => 1925
[authorName] => Kafka
)
```

# Exercise 2 Solution

The important thing to realize a Minefield is that the minefield is a two-dimensional grid, and you need a two-dimensional array to store it. Here's a possible solution:

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Creating a Minefield</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Creating a Minefield</h1>
</body>
</html>

<?php

$mineSize = 20;
$numMines = 10;
$minefield = array();
```