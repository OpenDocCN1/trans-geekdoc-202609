# Part III: Using PHP in Practice

```
((|\.).[A-Za-z\d]+)* # followed 0 or more times by (- or and more
# alphanumerics)
\.[A-Za-z\d]+$ # followed by a final dot and alphanumerics
$ # End of string
/x";
$phoneNumberPattern = "/
^ # Start of string
(
# Optional area code followed by optional
# separator:
(\d(3)\[[-. ? # Code with parentheses
# or
\d(3)[-. ? # Code without parentheses
)?
\d(3)
[-.]
\d(4) # Prefix
# Hyphen or dot separator
# Line number
$/x";
$productCodePattern = "^/(SW|MW|WW)(\d(2))$/i";nif (!preg_match($emailAddressPattern, $_POST["emailAddress"])) {
$errorMessages[] = "Invalid email address";
if (!preg_match($phoneNumberPattern, $_POST["phoneNumber\])) {
$errorMessages[] = "Invalid phone number";
}
if ($errorMessages) {
    echo "<There was a problem with the form you sent:<ul>
";
    foreach ($errorMessages as $errorMessage) echo "<li>$errorMessage</li>";
    echo "</ul>
<p>Please take <a href="javascript:history.go(-1)">go back</a> and try
again.</p>";
} else {
    echo "<>Thanks for your order! You ordered the following items:<n<ul>
";
    $productCodes = preg_split(\\W+"/, $_POST["productCodes"], -1, PREG_SPLIT_NO_EMPTY);
    $products = preg_replace_callback($productCodePattern, function($product) {
        return expandProductCodes($product);
    }, $productCodes);
    foreach ($products as $product) echo "<li>$product</li>";
    echo "</ul>
";
}


function expandProductCodes($matches) {
```

566