
# "while" Statements

This section provides a tutorial example on how to use `while` statements to repeat execution of one or more statements while a specified condition is true.

To help us understand how `while` statements work, I wrote the following tutorial example PHP script:

```php
<?php
#  WhileStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $upperLimit = 20;
#
   print("\n Single-statement \"while\":\n");
   $sum = 0; $i = 0;
   while ($i<$upperLimit) $sum += ++$i;
   print("    Sum of 1 to 20: $sum\n");
#
   print("\n Multi-statement \"while\":\n");
   $i = 3;
   while ($i<$upperLimit) {
      $isPrime = true;
      $j = 2;
      while ($j<$i) {
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
         $j++;
      }
      if ($isPrime) print "   $i is a prime number.\n";
      $i++;
   }
#
   print("\n Multi-statement \"while ... endwhile\":\n");
   $i = 3;
   while ($i<$upperLimit):
      $isPrime = true;
      $j = 2;
      while ($j<$i):
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
         $j++;
      endwhile;
      if ($isPrime) print "   $i is a prime number.\n";
      $i++;
   endwhile;
?>
```

If you run this sample script, you should get:

```
herong> \php\php WhileStatements.php

 Single-statement "while":
    Sum of 1 to 20: 210

 Multi-statement "while":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.

 Multi-statement "while ... endwhile":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"for" Statements

# "for" Statements

This section describes how `for` statements works in PHP. One or more statements are repeatedly executed as long as the specified condition is true. `for` statements has extra expressions for loop initialization and loop control update.

The `for` statement is the most complex loop statement in PHP. There are 4 forms of `for` statements supported in PHP:

## 1. Empty-statement "for"

```
for (initial_expression; stop_condition; repeating_expression);
```

## 2. Single-statement "for"

```
for (initial_expression; stop_condition; repeating_expression)
   statement;
```

## 3. Multi-statement "for"

```
for (initial_expression; stop_condition; repeating_expression) {
   statement;
   statement;
   ...
}
```

## 4. Multi-statement "for ... endfor"

```
for (initial_expression; stop_condition; repeating_expression):
   statement;
   statement;
   ...
endfor;
```

All forms of `for` statements are executed like this:

**Step 1:** `initial_expression` is evaluated unconditionally. The `initial_expression` is usually used to assign the initial value to a loop control variable, like `$i=0`.

**Step 2:** Evaluate `stop_condition` as a Boolean value. The `stop_condition` is usually a comparison expression against the loop control variable, like `$i<100`.

**Step 3:** If `stop_condition` returns `TRUE`, continue with Step 5.

**Step 4:** If `stop_condition` returns `FALSE`, terminate the loop.

**Step 5:** Execute the statement or statements enclosed in the loop.

**Step 6:** Evaluate `repeating_expression`. The `repeating_expression` is usually an expression to increment the value of the loop control variable, like `$i++`.

**Step 7:** Continue with Step 2.

If you want to terminate the loop early, you can use the `break` statement inside the loop, which will terminate the loop immediately.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"for" Statement Examples

# "for" Statement Examples

This section provides a tutorial example on how to use `for` statements to repeatedly execute zero, one or more statements.

To help us understand how `for` statements work, I wrote the following tutorial example script:

```php
<?php
#  ForStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $upperLimit = 20;
#
   print("\n No-statement \"for\":\n");
   for ($sum = 0, $i = 0; $i<$upperLimit; $sum += ++$i);
   print("    Sum of 1 to 20: $sum\n");

   print("\n Single-statement \"for\":\n");
   for ($sum = 0, $i = 0; $i<$upperLimit; $i++) $sum += $i;
   print("    Sum of 0 to 19: $sum\n");
#
   print("\n Multi-statement \"for\":\n");
   for ($i=3; $i<$upperLimit; $i++) {
      $isPrime = true;
      for ($j=2; $j<=$i/2; $j++) {
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
      }
      if ($isPrime) print "   $i is a prime number.\n";
   }
#
   print("\n Multi-statement \"for ... endfor\":\n");
   for ($i=3; $i<$upperLimit; $i++):
      $isPrime = true;
      for ($j=2; $j<=$i/2; $j++):
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
      endfor;
      if ($isPrime) print "   $i is a prime number.\n";
   endfor;
?>
```

If you run this sample script, you should get:

```
herong> \php\php ForStatements.php

 No-statement "for":
    Sum of 1 to 20: 210

 Single-statement "for":
    Sum of 0 to 19: 190

 Multi-statement "for":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.

 Multi-statement "for ... endfor":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"do ... while" Statements

# "do ... while" Statements

This section describes how `do ... while` statements works in PHP. One or more statements are repeatedly executed as long as the specified condition is true.

PHP also supports a variation of the `while` statement called `do ... while` statement, with 2 forms:

## 1. Single-statement "do ... while"

```
do statement while (condition);
```

## 2. Multi-statement "do ... while"

```
do {
   statement;
   statement;
   ...
} while (condition);
```

All forms of `do ... while` statements are executed like this:

**Step 1:** Execute the statement or statements enclosed in the loop.

**Step 2:** Evaluate `condition` as a Boolean value.

**Step 3:** If `condition` returns `TRUE`, continue with Step 1.

**Step 4:** If `condition` returns `FALSE`, terminate the loop.

Of course, you can use the `break` statement inside the loop to terminate the loop immediately.

I will leave it to you to write some sample scripts for `do ... while` statements as exercises.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"break" and "continue" Statements

# "break" and "continue" Statements

This section describes how `break` and `continue` statements works in PHP. `break` statement breaks the statement block and the loop. `continue` statement breaks the statement block, but continues on the next iteration of the loop.

In order to help us control the execution flow better, PHP provides two special statements, `break` and `continue`, for statement blocks:

## 1. "break" statement with no option

It breaks the current statement block and the current loop where the `break` statement is located. The remaining statements in the current statement block will not be executed. If current statement block is running as a loop, the loop will also be terminated.

```
any_block {
   ...
   any_block {
      ...
      any_block {
         ...
         break;
         ...
      }
      ...
   }
   ...
}
```
