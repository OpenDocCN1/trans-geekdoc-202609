# # Adding Products

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