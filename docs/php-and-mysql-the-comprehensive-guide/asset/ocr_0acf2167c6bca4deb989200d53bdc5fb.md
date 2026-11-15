# Generators

Generators are basically functions that are used in a `foreach` loop and return not just once, but several times. Instead of `return`, the `yield` keyword is used.

The following example defines a function that adds the numbers between a start and an end number. The increment can be selected via a separate parameter. All partial results of a loop are returned via yield.

```
<?php
function add($start, $end, $step = 1) {
 if ($start < $end) {
  $result = 0;
  for ($i = $start; $i <= $end; $i += $step) {
   $result += $i;
   yield $result;
  }
 }
}

foreach (add(2, 10, 2) as $result) {
 echo $result . '<br />';
}
?>
```

Listing 6.20 The Use of a Generator for Iteration ("function_generator.php")

In the example, the results are output directly (see Figure 6.12). However, they could also be used to fill an array directly, for example. The advantage of the generator is that you can iterate over data without having to store all the data in an array. The latter can fill up the working memory with large amounts of data.

![](bbox=[0.141, 0.618, 0.671, 0.773])

Figure 6.12 Here You Can Watch the Addition Process

# Static Variables

A local variable—that is, a variable that only exists within a function—is reset each time the function is called. This is why the counter had to be passed as a parameter in the example with the factorial from the last section.