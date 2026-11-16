locale() also builds a key that will be used later to look up the right format in the array. The key is built by concatenating the different variables that are used to select the format string. This technique makes the code more compact than if we had used if and case statements. This way, each character in the key corresponds to a different choice.

If the first character is 1, then $(n|p)_cs_precedes was true, meaning that the currency symbol should precede the number. Therefore, we see that $currency_symbol comes before %s in all the format strings that have a key that starts with 1. %s will be replaced by the actual number when the format string is used a little later in the function:

```
```php
if ($amount < 0) {
    $sign = $negative_sign;
    /* The following statements "extracts" the boolean value as an
    integer */
    $n_cs_precedes = intval($n_cs_precedes == true);
    $n_sep_by_space = intval($n_sep_by_space == true);
    $key = $n_cs_precedes . $n_sep_by_space . $n_sign_posn;
} else {
    $sign = $positive_sign;
    $p_cs_precedes = intval($p_cs_precedes == true);
    $p_sep_by_space = intval($p_sep_by_space == true);
    $key = $p_cs_precedes . $p_sep_by_space . $p_sign_posn;
}
```
```

```
```php
$formats = array(
    // Currency symbol is after amount
    // No space between amount and sign.
    '000' => '%s' . $currency_symbol . '),
    '001' => $sign . '%s' . $currency_symbol,
    '002' => '%s' . $currency_symbol . $sign,
    '003' => '%s' . $sign . $currency_symbol,
    '004' => '%s' . $sign . $currency_symbol,

    // One space between amount and sign.
    '010' => '%s' . $currency_symbol . '),
    '011' => $sign . '%s' . $currency_symbol,
    '012' => '%s ' . $currency_symbol . $sign,
    '013' => '%s ' . $sign . $currency_symbol,
    '014' => '%s ' . $sign . $currency_symbol,

    // Currency symbol is before amount
    // No space between amount and sign.
    '100' => '(' . $currency_symbol . '%s),
    '101' => $sign . $currency_symbol . '%s',
    '102' => $currency_symbol . '%s' . $sign,
    '103' => $sign . $currency_symbol . '%s',
    '104' => $currency_symbol . $sign . '%s',

    // One space between amount and sign.
    '110' => '(' . $currency_symbol . '%s),
    '111' => $sign . $currency_symbol . '%s',
    '112' => $currency_symbol . '%s' . $sign,
    '113' => $sign . $currency_symbol . '%s',
    '114' => $currency_symbol . '' . $sign . '%s');
```
```

// We then lookup the key in the above array.