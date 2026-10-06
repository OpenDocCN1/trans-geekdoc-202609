# Appendix A: Solutions to Exercises

# Chapter 9

# Exercise 1 Solution

To write number guessing game, you can make use of hidden fields to store both the number the computer is thinking of, and the number of guesses left. Here's how you could do it:

```
<!DOCTYPE html "-//W3C//DTD XHTML 1.0 Strict//EN"
" PUBLIC "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">\n<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <title>Guess the Number</title>
    <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
    <h1>Guess the Number</h1>

<?php

if ( isset($_POST["submitButton"]) ) && isset($_POST["guess"]) ) {
    processForm();
} else {
    displayForm(rand( 1, 100 ) );
}

function processForm() {
    $number = (int)$_POST["number"];
    $guessesLeft = (int)$_POST["guessesLeft"] - 1;
    $guess = (int)$_POST["guess"];

    if ($guess == $number) {
        displaySuccess($number);
    } elseif ($guessesLeft == 0) {
        displayFailure($number);
    } elseif ($guess < $number) {
        displayForm($number, $guessesLeft, "Too low - try again!");
    } else {
        displayForm($number, $guessesLeft, "Too high - try again!");
    }
}

function displayForm($number, $guessesLeft=5, $message=""") ) {
?>
    <form action=""" method="post">
    <div>
```

689