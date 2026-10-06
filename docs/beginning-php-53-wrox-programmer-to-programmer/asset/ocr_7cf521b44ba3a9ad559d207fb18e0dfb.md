# Part III: Using PHP Practice

If one or more error messages were generated, they were displayed to the user:

```
if ($errorMessages) {
    echo '<p>There was a problem with the form you sent:</p><ul>';
    foreach ($errorMessages as $errorMessage) echo '<li>$errorMessage</li>';
    echo '<p>Please <a href="javascript:history.go(-1)">go back</a> and try again.</p>';
}
```

If all went well, a thank-you message is displayed, and the list of ordered products is shown in the example below:

```
else {
    echo '<p>Thanks for your order! You ordered the following:</p><ul>';
    $productCodes = preg_split('/\W+/', $_POST['productCodes'], -1, PREG_SPLIT_NO_EMPTY);
    $products = preg_replace_callback($productCodePattern, 'expandProductCodes', $productCodes);
    foreach ($products as $product) echo '<li>$product</li>';
    echo '</ul>';
}
```

First, preg_split() is used to split the product code string into an array of individual product codes. The delimiter is one or more non-word characters (W+). This allows a degree of flexibility; for example, the user can use a comma to separate the codes, or a comma by a space, or a hyphen.

Next the array of product codes is processed by preg_replace_callback() to turn them into an array of names ($products). The product code regular expression created earlier ($productPattern) is used to match the two portions of the product code. The expansion is handled by the expandProductCodes function, which is explained in a moment.

Finally, the function loops through the $products array, displaying the product names in an unordered list.

The expandProductCodes() function defines an array to map the two-letter portion of the product code to a name:

```
$productCodes = array(
    "SW" => "SuperWidget",
    "MW" => "MegaWidget",
    "WW" => "WonderWidget"
);
```

Then it's simply a case of using the array to convert the first substring — $matches[1] — to the product name string, returning this string, followed by the string “model #”, followed by the second subpattern match, which is $matches[2]:

```
return $productCodes[$matches[1]] . " model #" . $matches[2];
```

570