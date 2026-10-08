'||.$products[$row]['Price']|<br />;

}

Using for a loop, you can step through the outer, numerically indexed $products array. Each row in the $products array is an array with indices. Using the each() and list() functions in a while loop, you can step through these inner arrays. Therefore, you can use a while loop inside a for loop:

```
for ($row = 0; $row < 3; $row++) {
    while (list($key, $value) = each($products[$row])) {
        echo '||.$value;';
    }
    echo '<br />';
}
```

You do not need to stop at two dimensions. In the same way that array elements can hold new arrays, those arrays, in turn, can hold more arrays.

A three-dimensional array has height, width, and depth. If you are comfortable thinking of a two-dimensional array as a table with rows and columns, imagine a pile or deck of tables. Each element is referenced by its layer, row, and column.

If Bob divided his products into categories, you could use a three-dimensional array to store them. Figure 3.4 shows Bob's products in a three-dimensional array.

| Truck Parts | | | |
| Code | Description | Price | |
| Van Parts | | | |
| Code | Description | Price | |
| Car Parts | | | |
| Code | Description | Price |
| CAR_TIR | Tires | 100 |
| CAR_OIL | Oil | |
| CAR_SPK | Spark Plugs | 4 |

Figure 3.4 This three-dimensional array allows you to divide products into categories