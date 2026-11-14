```
SELECT CONCAT("C", sc.id), c.quantity, gc.category,
CONCAT_WS(" - ", s.size, sc.caf_decaf, sc.ground_whole), sc.price,
sc.stock, sales.price
FROM carts AS c
INNER JOIN specific_coffees AS sc ON c.product_id=sc.id
INNER JOIN sizes AS S ON s.id=sc.size_id
INNER JOIN general_coffees AS gc ON gc.id=sc.general_coffee_id
LEFT OUTER JOIN sales ON
(sales.product_id=sc.id AND sales.product_type='coffee' AND
((NOW() BETWEEN sales.start_date AND sales.end_date) OR (NOW() >
sales.start_date AND sales.end_date IS NULL)))
WHERE c.product_type="coffee" AND c.user_session_id=uid;
END$$
DELIMITER ;
```

Figure 9.2 shows the result of calling this procedure. You’ll notice that the query returns the default price (under the heading _price_), the quantity in stock, and the sale price, if any. This information will be needed later.

![](bbox=[0.31, 0.47, 0.68, 0.57])

Figure 9.2

# # DEFINING THE HELPER FUNCTIONS

Before getting into the shopping cart itself, there are two helper functions that will be useful to this chapter’s code. The first function takes two possible prices—the regular and the sale price—and returns the appropriate price for the product:

```
function get_just_price($regular, $sales) {
if ((0 < $sales) && ($sales < $regular)) {
return number_format($sales, 2);
} else {
return number_format($regular, 2);
}
}
```