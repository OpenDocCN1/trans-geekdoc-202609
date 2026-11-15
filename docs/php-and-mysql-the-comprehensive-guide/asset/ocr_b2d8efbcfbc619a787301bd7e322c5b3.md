However, preg_match_all(RegEx, String, Variable, Mode) has other values for the mode: PREG_PATTERN_ORDER and PREG_SET_ORDER. You can combine both with PREG_OFFSET_CAPTURE by writing the modes one after the other, separated by |. The default is PREG_PATTERN_ORDER if the specification is missing. The patterns found are saved as an array in the first array element of the variable (index 0). In the second and subsequent elements, the locations for parts of the pattern divided by brackets are specified.

Here is a small example to illustrate this:

```
$text = "Otto";
$reg = "/(Ot|ot)|(to|t0)/";
preg_match_all($reg, $text, $parts, PREG_PATTERN_ORDER);
```

This returns 0t and to as the result of all pattern checks. The individual areas each provide one result (see Figure 10.4).

![](bbox=[0.145, 0.365, 0.785, 0.48])

# Figure 10.4 The Individual Components

PREG_SET_ORDER, on the other hand, orders the results so that the first array element corresponds to the results of the first bracket, the second to those of the second, and so on (see Figure 10.5).

```
<?php
$text = "Otto";
$reg = "/(Ot|ot)|(to|t0)/";
preg_match_all($reg, $text, $teile, PREG_SET_ORDER);
print_r($parts);
?>
```

# Listing 10.4 Options for "preg_match_all()" ("preg_match_all_opt.php")

![](bbox=[0.145, 0.755, 0.785, 0.87])

# Figure 10.5 The Two Results of the Individual Components