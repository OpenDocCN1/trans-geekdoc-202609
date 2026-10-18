# FIGURE 9.7 The ‘switch’ construct

![](bbox=[0.2, 0.08, 0.92, 0.33])

The ‘switch’ construct consists of a ‘switch’ component in which an expression is evaluated. The result of the expression is then compared in turn to a list of ‘case’ statements. The first ‘case’ value which matches to the expression determines which associated statements are executed.

> NOTE While you can implement the ‘switch’ construct using a number of ‘if’ statements the code can become complex and difficult to understand.

Figure 9.7 illustrates the ‘switch’ construct.

> NOTE Note the use of the braces to surround the ‘switch’ structure.

The following script illustrates the use of the ‘switch’ construct:

```
<?php
// File: example9-7.php

$strName = "Elizabeth";

switch ($strName) {
case "Simon":
    echo "<p>Hello Simon</p>";
case "Elizabeth":
    echo "<p>Hello Elizabeth</p>";
case "Hayley":
    echo "<p>Hello Hayley</p>";
case "Alan":
    echo "<p>Hello Alan</p>";
}
?>
```

In the above example there are four cases which display a message depending on the value of variable $strName. The output from the above script is shown in Figure 9.8. Interestingly, the output may not be what you were expecting. Instead of simply displaying the text