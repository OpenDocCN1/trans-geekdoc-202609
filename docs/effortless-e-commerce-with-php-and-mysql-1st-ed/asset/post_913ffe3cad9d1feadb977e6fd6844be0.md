
## Adding Products

The `add_to_cart()` stored procedure will be invoked when the customer requests that a product be added to their shopping cart. The procedure needs to take four pieces of information — a unique user ID, the product type (`coffee` or `other`), the product ID, and the quantity being added. As an extra bit of logic, the procedure should `add` the product to the cart if it doesn’t already exist there but `add` more quantity of the product if it is already in the cart. Here is the stored procedure, and I’ll explain its logic afterward:

```
DELIMITER $$
CREATE PROCEDURE add_to_cart (uid CHAR(32), type VARCHAR(6), pid MEDIUMINT, qty TINYINT)
BEGIN
DECLARE cid INT;
SELECT id INTO cid FROM carts WHERE user_session_id=uid AND
product_type=type AND product_id=pid;
IF cid > 0 THEN
UPDATE SET quantity=quantity+qty, date_modified=NOW()
WHERE id=cid;
ELSE
INSERT INTO carts (user_session_id, product_type, product_id,
quantity) VALUES (uid, type, pid, qty);
END IF;
END$$
DELIMITER ;
```

> See Chapter 8 for instructions on creating stored procedures in your database.

> You can download all the SQL and files for this project from www.DMCInsights.com/ecom/.

First, in keeping with how stored procedures are created, the delimiter is immediately changed to the combination of two dollar signs together. Next, the procedure’s `signature` is created, which is to say the combination of its name and arguments. The first argument is the user’s session ID, which will be exactly 32 characters long. Next is the product type, which will be either five or six characters long (`other` or `coffee`). The last two arguments are the product’s ID and the quantity being added.

> The delimiter just needs to be changed to something other than a semicolon.

To incorporate the logic that checks if the product is already in the cart, an internal variable is necessary. You can create one using `DECLARE`, followed by the variable’s name and its MySQL data type. The variable named `cid` is created, short for `cart ID`.

> Variables must be declared immediately after the `BEGIN` statement.

Next, a `SELECT` query checks the `carts` table for the submitted product. If the product is already represented in the table, then its `id` value will be assigned to the `cid` variable, thanks to the `SELECT...INTO` syntax.

After the **SELECT** query, an IF-ELSE conditional will run either an **UPDATE** or an **INSERT** query, depending upon the value of cid. If it's greater than zero, then the product is already in the table, and the submitted quantity should be added to the existing quantity. Otherwise, a new record is inserted. The **date_modified** column is updated to the current moment only for an **UPDATE** query.

> **tip**
> The arguments passed to a stored procedure can be used internally in queries as if the queries were prepared statements, meaning that strings need not be quoted.

## Removing Products

The stored procedure for removing products from the cart is the simplest of the four procedures. It requires three of the four arguments that **add_to_cart()** uses (obviously no quantity needs to be indicated when removing something). The procedure just runs a **DELETE** query:

```
DELIMITER $$
CREATE PROCEDURE remove_from_cart (uid CHAR(32), type VARCHAR(6),
    pid MEDIUMINT)
BEGIN
    DELETE FROM carts WHERE user_session_id=uid AND product_type=type
    AND product_id=pid;
END$$
DELIMITER ;
```

## Updating the Cart

> **tip**
> The site offers two ways to remove items from the cart: clicking a link and entering zero for the quantity.

The stored procedure for updating the shopping cart will be invoked after the user clicks the update button on the shopping cart page (Figure 9.1). The procedure takes the same four arguments as **add_to_cart()**, but doesn't have to confirm that the product already exists in the database (unless the user did something tricky, the product has to exist in order to show up in the cart form). However, if the user enters zero for the quantity of the item, the procedure should go ahead and remove that from the cart. Rather than write the removal functionality into this procedure, the procedure will just invoke the already defined remove_from_cart() procedure if the quantity is zero.

```
DELIMITER $$
CREATE PROCEDURE update_cart (uid CHAR(32), type VARCHAR(6), pid MEDIUMINT, qty TINYINT)
BEGIN
	If qty > 0 THEN
		UPDATE carts SET quantity=qty, date_modified=NOW() WHERE
		user_session_id=uid AND product_type=type AND product_id=pid;
	ELSEIF qty = 0 THEN
		CALL remove_from_cart (uid, type, pid);
	END IF;
END$$
DELIMITER ;
```

> Whenever the quantity of an item in the carts or wish_lists table changes (without the product being removed), the item's date_modified value is updated, too.

## Fetching the Cart's Contents

The fourth and final stored procedure (for the shopping cart, that is) runs a SELECT query to retrieve all the contents of the cart. How tricky this SELECT query is depends upon how much information you want to display, but at its base, the query looks a lot like the sales-related queries from Chapter 8. The query is a UNION of two SELECT statements: the first a JOIN across four tables and the second a JOIN across five. In the procedure, I've written out the query over multiple lines for clarity. This procedure only needs the user's session ID as an argument.

```
DELIMITER $$
CREATE PROCEDURE get_shopping_cart_contents (uid CHAR(32))
BEGIN
	SELECT CONCAT("O", ncp.id) AS sku, c.quantity, ncc.category,
	ncp.name, ncp.price, ncp.stock, sales.price AS sale_price
	FROM carts AS c
	INNER JOIN non_coffee_products AS ncp ON c.product_id=ncp.id
	INNER JOIN non_coffee_categories AS ncc ON ncc.id=ncp.non_coffee_category_id
	LEFT OUTER JOIN sales ON
	(sales.product_id=ncp.id AND sales.product_type='other' AND
	((NOW() BETWEEN sales.start_date AND sales.end_date) OR (NOW() >
	sales.start_date AND sales.end_date IS NULL))) )
	WHERE c.product_type="other" AND c.user_session_id=uid
	UNION
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

Figure 9.1

![](img/4f47e47c67bd619ac73250f11c9fc7ce_248_0.png)

Figure 9.2 shows the result of calling this procedure. You’ll notice that the query returns the default price (under the heading _price_), the quantity in stock, and the sale price, if any. This information will be needed later.

![](img/4f47e47c67bd619ac73250f11c9fc7ce_250_0.png)

Figure 9.2

## DEFINING THE HELPER FUNCTIONS

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

This is similar to the get_price() function already defined in Chapter 8, but just returns the numeric price (get_price()) returned the price within some context).

The second function will parse a SKU, which is to say convert a value like C12 into coffee and 12, accordingly. This conversion will often be necessary, because the database uses each product's type and ID number individually. The function for parsing the SKU takes one argument—the SKU itself—and returns an array containing two elements:

```
function parse_sku($sku) {
// Grab the first character:
$type_abbr = substr($sku, 0, 1);

// Grab the remaining characters:
$pid = substr($sku, 1);

// Validate the type:
if ($type_abbr == 'C') {
$sp_type = 'coffee';
} elseif ($type_abbr == 'O') {
$sp_type = 'other';
} else {
$sp_type = NULL;
}

// Validate the product ID:
$pid = (filter_var($pid, FILTER_VALIDATE_INT, array('min_range' => 1)))
? $pid : NULL;

// Return the values:
return array($sp_type, $pid);
} // End of parse_sku() function.
```

The two uses of substr() breaks the SKU into its parts. Next, the product type is validated based upon the first character in the SKU, which must be either C, for coffee, or O, for other. If neither is the case, the $sp_type variable is assigned the value NULL.

The remaining characters must be an integer greater than 1. The filter_var() function can test for that. If the value is an integer greater than 1, the value is assigned to $pid. Otherwise, the value NULL will be assigned.
