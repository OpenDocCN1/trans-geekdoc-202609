# Part II: Learning the Language

Incidentally, you can also use a numeric argument with break in this way to break out of nested switch constructs (or, for example, a switch embedded within a while or for loop).

# Try Out

# A Homing Pigeon Simulation

Here's an example script that brings together some of the concepts you've learned in this chapter so far. The script graph simulates the path of a homing pigeon as it flies from its starting point to its home. We're not talking 3-dimensional animated graphs here, but it gets the idea across!

Here's the script in all its glory:

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
<a href="http://www.w3.org/TR/html/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>Homing Pigeon Simulation</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
  <style type="text/css">
    div.map { float: left; text-align: center; border: 1px solid #666;
      background-color: #fcfcfc; margin: 5px; padding: 1em; }
    span.home, span.pigeon { font-weight: bold; }
    span.empty { color: #666; }
  </style>
</head>
<body>

<?php
$mapSize = 10;

// Position the home and the pigeon

do {
  $homeX = rand ( 0, $mapSize-1 );
  $homeY = rand ( 0, $mapSize-1 );
  $pigeonX = rand ( 0, $mapSize-1 );
  $pigeonY = rand ( 0, $mapSize-1 );
} while ( abs ($homeX - $pigeonX) < $mapSize/2 ) && ( abs ($homeY - $pigeonY) < $mapSize/2 );

do {
  // Move the pigeon closer to the home

  if ($pigeonX < $homeX) {
    $pigeonX++;
  } elseif ($pigeonX > $homeX) {
    $pigeonX--;
  }

  if ($pigeonY < $homeY) {
    $pigeonY++;
```