```
<?php
nfunction multiplier($a, $b) {
    return $a * $b;
}

echo multiplier((int)2,(int)4); // Output '8'

echo multiplier((float)2.5, (float)6.0); // Output '15'

echo multiplier('abc', 5); // Output '0'
```

The function illustrated above can be considered to support parametric polymorphism since it will execute successfully irrespective of the data types of the input parameters. Quite you consider the attempt to multiply the string abc by 5 to be a successful execution is up to you. Nevertheless, on the face of it, the function is called three times with different sets of input parameters and subsequently emits a return value without complaint.

From an object oriented programming perspective though, we should consider parametric polymorphism to be thus:

> Parametric polymorphism is a way to make a language more expressive, while still maintaining full type-safety. Using parametric polymorphism, a function or a data type can be written generically so that it can handle values identically depending on their type. Such functions and data types are called generic functions and generic datatypes respectively and form the basis of generic programming. - Wikipedia

For the benefit of our discussion here in the glorious world of PHP we can explore the wondrous world of parametric polymorphism only by flipping our point of view and switching our attention from provider to consumer. What do I mean by that? Well, in the preceding sections on Ad Hoc and Subtype Polymorphism, I've been focussing our attention on the provider side of the equation. The java example given in the Ad Hoc section provided multiple definitions of the Add() method and allowed the compiler to select the most appropriate definition based on the