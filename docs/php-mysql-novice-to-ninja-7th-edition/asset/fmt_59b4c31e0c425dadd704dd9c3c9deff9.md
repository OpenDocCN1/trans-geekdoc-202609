
You can also add elements to the end of an array using the assignment operator as usual, but leaving empty the square brackets that follow the variable name:

```
$myArray[] = 'five';
echo $myArray[4];    // outputs 'five'
```

Array elements can be used like any other variable, and in a lot of cases choosing to use an array or multiple variables will depend on the programmer’s preference. However, arrays can be used to solve problems that normal variables can’t!

Remember the dice game from the last section? It would be more user-friendly if it showed the English word rather than the numeral for the result. For example, instead of “You rolled a 3” or “You rolled a 6”, it might be nicer to read “You rolled a three” or “You rolled a six”.

To do this, we need some way of converting from a numeral to the English word for that number. This is possible with a series of `if` statements.

**Example: [PHP-DiceRoll-English-If](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-English-If)**

```
$roll = rand(1, 6);

if ($roll == 1) {
  $english = 'one';
}
else if ($roll == 2) {
  $english = 'two';
}
else if ($roll == 3) {
  $english = 'three';
}
else if ($roll == 4) {
  $english = 'four';
}
else if ($roll == 5) {
  $english = 'five';
}
else if ($roll == 6) {
  $english = 'six';
}

echo '<p>You rolled a ' . $english . '</p>';

if ($roll == 6) {
  echo '<p>You win!</p>';
}
else {
  echo '<p>Sorry, you didn\'t win. Better luck next time!</p>';
}*
```

This solution works, but it’s very inefficient, as you need to write an `if` statement for each possible dice roll. Instead, you can use an array to store each roll value:

```
$english = [
  1 => 'one',
  2 => 'two',
  3 => 'three',
  4 => 'four',
  5 => 'five',
  6 => 'six'
];
```

The `=>` notation (known as a **double arrow operator**) allows you to define both the keys and the values when creating the array. This is equivalent to the following:

```
$english = [];
$english[1] = 'one';
$english[2] = 'two';
$english[3] = 'three';
$english[4] = 'four';
$english[5] = 'five';
$english[6] = 'six';
```

Although these are equivalent, the code required to use the shorthand notation is a lot quicker to type, and is arguably easier to read and easier to understand.

Now that the array is created, it’s possible to read each English word from it:

```
echo $english[3];    // Prints "three"
echo $english[5];    // Prints "five"
```

In PHP, a number like `3` can be replaced with a variable that contains that value. This is also possible with array keys. For example:

```
$var1 = 3;
$var2 = 5;

echo $english[$var1];    // Prints "three"
echo $english[$var2];    // Prints "five"
```

Knowing this, we can piece it all together and adjust the dice game to display the English word of the dice roll by reading the relevant value from the array using the `$roll` variable.

**Example: [PHP-DiceRoll-English-Array](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-English-Array)**

```
$english = [
  1 => 'one',
  2 => 'two',
  3 => 'three',
  4 => 'four',
  5 => 'five',
  6 => 'six'
];

$roll = rand(1, 6);

echo '<p>You rolled a ' . $english[$roll] . '</p>';

if ($roll == 6) {
  echo '<p>You win!</p>';
}
else {
  echo '<p>Sorry, you didn\'t win, better luck next time!</p>';
}
```

As you can see, this is a lot cleaner and tidier than a long list of `if` statements. There are two big advantages here.

Firstly, if you wanted to represent a ten-sided dice, it’s a lot easier to add to the array than add an extra `if` statement for each number.

Secondly, the array is reusable. For the version with two dice, you can just reuse the `$english` array rather than repeating all the `if` statements for each dice roll.

**Example: [PHP-DiceRoll-English-If-TwoDice](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-English-If-TwoDice)**

```
$roll1 = rand(1, 6);
$roll2 = rand(1, 6);

if ($roll1 == 1) {
  $english = 'one';
}
else if ($roll1 == 2) {
  $english = 'two';
}
else if ($roll1 == 3) {
  $english = 'three';
}
else if ($roll1 == 4) {
  $english = 'four';
}
else if ($roll1 == 5) {
  $english = 'five';
}
else if ($roll1 == 6) {
  $english = 'six';
}

if ($roll2 == 1) {
  $englishRoll2 = 'one';
}
else if ($roll2 == 2) {
  $englishRoll2 = 'two';
}
else if ($roll2 == 3) {
  $englishRoll2 = 'three';
}
else if ($roll2 == 4) {
  $englishRoll2 = 'four';
}
else if ($roll2 == 5) {
  $englishRoll2 = 'five';
}
else if ($roll2 == 6) {
  $englishRoll2 = 'six';
}

echo '<p>You rolled a ' . $english . ' and a ' . $englishRoll2 . '</p>';
```

Instead, the array can be used for both rolls.

**Example: [PHP-DiceRoll-English-Array-TwoDice](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-English-Array-TwoDice)**

```
$english = [
  1 => 'one',
  2 => 'two',
  3 => 'three',
  4 => 'four',
  5 => 'five',
  6 => 'six'
];

$roll1 = rand(1, 6);
$roll2 = rand(1, 6);

echo '<p>You rolled a ' . $english[$roll1] . ' and a ' . $english[$roll2] . '</p>';
```

While numbers are the most common choice for array indices, there’s another possibility. You can also use strings as indices to create what’s called an **associative array**. It’s called this because it *associates* values with meaningful indices. In this example, we associate a date (in the form of a string) with each of three names:

```
$birthdays['Kevin'] = '1978-04-12';
$birthdays['Stephanie'] = '1980-05-16';
$birthdays['David'] = '1983-09-09';
```

Like the numerical indexes, you can use the shorthand notation for associative arrays as well:

```
$birthdays = [
  'Kevin' => '1978-04-12',
  'Stephanie' => '1980-05-16',
  'David' => '1983-09-09'
];
```

Now, if we want to know Kevin’s birthday, we look it up using the name as the index:

```
echo 'Kevin\'s birthday is: ' . $birthdays['Kevin'];
```

This type of array is especially important when it comes to user interaction in PHP, as we’ll see shortly. I’ll also demonstrate other uses of arrays throughout this book.

### Escaping the Apostrophe

Because `Kevin's` contains an apostrophe (single quote) and PHP would see this as the end of the string, it must be escaped with a `\` so that PHP treats it as part of the string, rather than marking the end.

## User Interaction and Forms

Database-driven websites often need to do more than dynamically generate pages based on database data. You also need to provide some degree of interactivity, even if it’s just a search box.

Because JavaScript code can live in the browser, it allows users to have all sorts of immediate interactions with a web page. Server-side scripting languages such as PHP have a more limited scope when it comes to support for user interaction. As PHP code is only activated when a request is made to the server, user interaction occurs solely in a back-and-forth fashion: the user sends requests to the server, and the server replies with dynamically generated pages.

The key to creating interactivity with PHP is to understand the techniques we can employ to send information about a user’s interaction, along with a request for a new web page. As it turns out, PHP makes this quite easy.

### JavaScript and Interactivity

As the Web has evolved, so too have the options for communication between the front and back ends of a web app. JavaScript allows for communication with a back end without page reloading. A JavaScript framework such as Vue.js, for example, can communicate with PHP frameworks like Laravel. For the purposes of this book, however, we’ll focus on what can be done with PHP alone.

### Passing Variables in Links

The simplest way to send information along with a page request is to use the URL query string. If you’ve ever noticed a URL containing a question mark that follows the filename, you’ve seen this technique in use. For example, if you search for “SitePoint” on Google, it will take you to a search result page with a URL like this:

```
http://www.google.com/search?hl=en&q=SitePoint
```
