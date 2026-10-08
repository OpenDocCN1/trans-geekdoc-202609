# Working Out the Form Totals

Now that you know how to use PHP's operators, you are ready to work out the totals and tax on Bob's order form. To do this, add the following code to the bottom of your PHP script:

```
$totalqty = 0;
$totalqty = $tireqty + $oilqty + $sparkqty;
echo $item->Items ordered: ".$totalqty.".<br />";
$totalamount = 0.00;
```

```
define('TIREPRICE', 100);
define('OILPRICE', 10);
define('SPARKPRICE', 4);
```

```
$totalamount = $tireqty * TIREPRICE
+ $oilqty * OILPRICE
+ $sparkqty * SPARKPRICE;
```

```
echo "Subtotal: ".number_format($totalamount,2)."<br />";
```

```
$taxrate = 0.10; // local sales tax is 10%
$totalamount = $totalamount * (1 + $taxrate);
echo "Total including tax: ".number_format($totalamount
```

If you refresh the page in your browser window, you should see output similar to Figure 1.5.
As you can see, this piece of code uses several operators. It uses the addition (+) and multiplication (*) to work out the amounts and the string concatenation operator (.) to set up the output to the browser.

![](bbox=[0.118, 0.606, 0.606, 0.866])

Figure 1.5 The totals of the customer's order have been calculated, formatted, and displayed