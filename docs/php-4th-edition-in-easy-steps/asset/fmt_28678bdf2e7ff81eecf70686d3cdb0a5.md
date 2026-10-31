
You can nest conditional `if` tests (one inside another) so that statements in the inner block only get executed when both tests are found to be `TRUE`.

## Switching branches

![image](images/pg62_1.jpg)

Conditional branching performed by multiple if-elseif-else statements can often be performed more efficiently by a `switch` statement when the test expression just evaluates one condition.

The `switch` statement works in an unusual way. It takes a given value as its parameter argument then seeks to match that value from a number of `case` statements. Code to be executed when a match is found is included in each `case` statement.

It is important to end each `case` statement with a `break` keyword statement, so the `switch` statement will then exit when a match is found without seeking further matches – unless that is the deliberate requirement.

Optionally, the list of `case` statements can be followed by a single final `default` statement to specify code to be executed in the event that no matches are found within any of the `case` statements. So the syntax of a `switch` statement typically looks like this:

```
switch ( test-value )
{
case match-value : statements-to-execute-when-matched ; break ;
case match-value : statements-to-execute-when-matched ; break ;
case match-value : statements-to-execute-when-matched ; break ;
default : statements-to-execute-when-no-match-found ;
}
```

A `switch` statement can have many `case` statements, but no two of its `case` statements can attempt to match the same value.

![image](images/hot.jpg)

It’s always a good idea to include a `default` statement – even if it’s only to output an error message when the `switch` statement fails.

Where a number of match-values are to each execute the same statements, only the final `case` statement need include the statements to be executed and the `break` statement to exit the `switch` statement block. For example, to output the same message for match-values of 0, 1 and 2:

```
switch ( $number )
{
case 0 :
case 1 :
case 2 : echo ‘Less than 3’ ; break ;
case 3 : echo ‘Exactly 3’ ; break ;
default : echo ‘Greater than 3 or less than zero’ ;
}
```

![image](images/forget.jpg)

A `default` statement need not appear at the end of the `switch` block, but it is logical to place it there where it needs no `break` statement.

![image](images/1p.jpg) Between PHP tags, begin a script with statements that initialize two variables with an integer and character value

```
<?php
$number \= 2 ; $letter \= ‘B’ ;
```

![image](images/commonp.jpg)

switch.php

![image](images/2p.jpg) Next, add a `switch` statement to match the integer value

```
switch ( $number )
{
case 1 : echo ‘Number is One<br>’ ; break ;
case 2 : echo ‘Number is Two<br>’ ; break ;
case 3 : echo ‘Number is Three<br>’ ; break ;
default : echo ‘Number is Unrecognized<br>’ ;
}
```

![image](images/3p.jpg) Now, add a `switch` statement to match the character value

```
switch ( $letter )
{
case ‘A’ : echo ‘Letter is A<br>’ ; break ;
case ‘B’ : echo ‘Letter is B<br>’ ; break ;
case ‘C’ : echo ‘Letter is C<br>’ ; break ;
default : echo ‘Letter is Unrecognized<br>’ ;
}
```

![image](images/4p.jpg) Finally, add a `switch` statement to match against multiple integer values

```
switch ( $number )
{
case 0 : case 1 : case 2 : echo ‘Less than 3<br>’ ; break ;
default : echo ‘3 or more, or less than zero’ ;
}
?>
```

![image](images/5p.jpg) Save the document in your web server’s `/htdocs` directory as `switch.php` then open the page via HTTP to see the results of conditional branching get displayed

![image](images/pg63_1.jpg)

![image](images/hot.jpg)

In `switch` statements, the `case` keyword, match-value and colon character are regarded as a unique “label”.

## Matching expressions

![image](images/pg64_1.jpg)

Conditional branching can also be performed by `match` statements. These are an alternative to the `switch` statements, described [hereon pages 62-63](#chapter04.xhtml#sec29), and may often be a better choice.

Unlike a `switch` statement block, a `match` statement is a single expression that returns a value. It takes a given value as its parameter argument then seeks to match that value from a comma-separated list of alternatives enclosed within curly brackets. The value to be returned when a match is found is then specified after a `=>` fat arrow operator.

It is important to end each `match` statement with a `;` semi-colon after the closing curly bracket to terminate the statement.

A `match` expression does not require any `break` statements so its code is significantly shorter than an equivalent `switch` block. The syntax of a `match` statement typically looks like this:

```
$result = match ( test-value )
{
match-value => return-value ,
match-value => return-value ,
match-value => return-value ,
default => return-value ,
} ;
```

![image](images/hot.jpg)

The `match` statement is a great new feature introduced in PHP 8.

Where a number of match-values are to each return the same value, they can be combined into a comma-separated single list. For example, to output the same message for match-values of 0, 1 and 2:

```
echo match ( $number )
{
0 , 1 , 2 => ‘Less than 3’ ,
3 => ‘Exactly 3’ ,
default => ‘Greater than 3 or less than zero’ ,
} ;
```

It is useful to recognize that a `match` statement compares values for identicality, like using the `===` operator, whereas a `switch` statement compares values for equality, like using the `==` operator.

The steps in the example opposite use `match` statements to replicate the output from the previous `switch` statement example.

![image](images/1p.jpg) Between PHP tags, begin a script with statements that initialize two variables with an integer and character value

```
<?php
$number \= 2 ; $letter \= ‘B’ ;
```

![image](images/commonp.jpg)

match.php

![image](images/2p.jpg) Next, add a `match` statement to match the integer value

```
echo match ( $number )
{
1 \=> ‘Number is One<br>’ ,
2 \=> ‘Number is Two<br>’ ,
3 \=> ‘Number is Three<br>’ ,
default => ‘Number is Unrecognized<br>’ ,
} ;
```

![image](images/3p.jpg) Now, add a `match` statement to match the character value

```
echo match ( $letter )
{
‘A’ \=> ‘Letter is A<br>’ ,
‘B’ \=> ‘Letter is B<br>’ ,
‘C’ \=> ‘Letter is C<br>’ ,
default => ‘Letter is Unrecognized<br>’ ,
} ;
```

![image](images/4p.jpg) Finally, add a `match` statement to match against multiple integer values

```
echo match ( $number )
{
0 , 1 , 2\=> ‘Less than 3<br>’ ,
default => ‘3 or more, or less than zero’ ,
} ;
?>
```

![image](images/5p.jpg) Save the document in your web server’s `/htdocs` directory as `match.php` then open the page via HTTP to see the results of conditional branching get displayed

![image](images/pg65_1.jpg)

![image](images/hot.jpg)

Compare the code in this example against the `switch` statements in the previous example to see the simplicity advantage of `match` statements.

## Performing loops

![image](images/pg66_1.jpg)

A loop is a piece of code in a script that automatically repeats. One complete execution of all statements within a loop is called an “iteration”, or a “pass”. The length of a loop is controlled by a conditional test made within the loop. While the tested expression is found to be `TRUE` the loop will continue – until the tested expression is found to be `FALSE` at which point the loop ends.

In PHP there are four types of loop structure:

• `for` loop – performs a specified number of iterations.
• `while` loop – performs iterations only while a test made at the start of each iteration evaluates as `TRUE`.
• `do while` loop – performs iterations only while a test made at the end of each iteration evaluates as `TRUE`.
