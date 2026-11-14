are displayed. For this reason, the sale price of each product type is treated
a bit differently.

+   4. Return the sale price, if appropriate:

```
if ((o < $$sales) & & ($sales < $regular)) {
return ' Sale: $' . $sales . '!';
}
```

The value of $sales will be NULL if no sale price exists (see Figure 8.17), so
this conditional confirms that the value is greater than zero but not greater
than the regular price (on account of some sort of administrative error). If
so, then the word Sale, followed by a colon and the sale price is returned
(for coffee products).

+   5. Check if the type equals goodies:

```
} elseif ($type == 'goodies') {
```

For the non-coffee products, the sale price can be displayed with more
information and flare.

+   6. Return the appropriate price:

```
if ((o < $$sales) && ($sales < $regular)) {
return "<strong>Sale Price:</strong> $$sales! (normally
$$regular)<br />";
} else {
return '<strong>Price:</strong> $' . $regular . ' <br />';
}
```

If the sale price is greater than zero but less than the regular price, the sale
price will be returned with the regular price in parentheses (so the customer
can see the extra value, Figure 8.16). Otherwise, just the regular price is
returned.

+   7. Complete the if-elseif conditional and the function definition:

```
}
} // End of get_price() function.
```

+   8. Save the file.

# # Updating list_products.html

For list_products.html to take advantage of the new function, you just need to
replace the reference to $row['price'] with:

```
get_sale_price($type, $row['price'], $row['sale_price'])
```