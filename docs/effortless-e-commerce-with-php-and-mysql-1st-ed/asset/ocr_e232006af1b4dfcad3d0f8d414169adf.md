functionality into this procedure, the procedure will just invoke the already defined remove_from_cart() procedure if the quantity is zero.

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

# Fetching the Cart's Contents

The fourth and final stored procedure (for the shopping cart, that is) runs a SELECT query to retrieve all the contents of the cart. How tricky this SELECT query is depends upon how much information you want to display, but at its base, the query looks a lot like the sales-related queries from Chapter 8. The query is a UNION of two SELECT statements: the first a JOIN across four tables and the second a JOIN across five. In the procedure, I've written out the query over multiple lines for clarity. This procedure only needs the user's session ID as an argument.

```
DELIMITER $$
CREATE PROCEDURE get_shopping_cart_contents (uid CHAR(32))
BEGIN
	SELECT CONCAT("O", ncp.id) AS sku, c.quantity, ncc.category,
	ncp.name, ncp.price, ncp.stock, sales.price AS sale_price
	FROM carts AS c
	INNER JOIN non_coffee_products AS ncp ON c.product_id=ncp.id
	INNER JOIN non_coffee_categories AS ncc ON ncc.id=ncp.non_coffee_
	category_id
	LEFT OUTER JOIN sales ON
	(sales.product_id=ncp.id AND sales.product_type='other' AND
	((NOW() BETWEEN sales.start_date AND sales.end_date) OR (NOW() >
	sales.start_date AND sales.end_date IS NULL))) )
	WHERE c.product_type="other" AND c.user_session_id=uid
	UNION
(continues on next page)
```