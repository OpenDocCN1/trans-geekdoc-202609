The complete stored procedure is therefore:

```
DELIMITER $$
CREATE PROCEDURE add_order (cid INT, uid CHAR(32), ship DECIMAL(5,2),
 cc MEDIUMINT, OUT total DECIMAL(7,2), OUT oid INT)
BEGIN
 DECLARE subtotal DECIMAL(7,2);
 INSERT INTO orders (customer_id, shipping, credit_card_number,
 order_date) VALUES (cid, ship, cc, NOW());
 SELECT LAST_INSERT_ID() INTO oid;
 INSERT INTO order_contents (order_id, product_type, product_id,
 quantity, price_per) SELECT oid, c.product_type, c.product_id,
 c.quantity, IFNULL(sales.price, c.price) FROM carts AS c INNER JOIN
 non_coffee_products AS ncp ON c.product_id=ncp.id LEFT OUTER JOIN
 sales ON (sales.product_id=ncp.id AND sales.product_type='other'
 AND ((NOW()) BETWEEN sales.start_date AND sales.end_date)
 OR (NOW() > sales.start_date AND sales.end_date IS NULL))) WHERE
 c.product_type="other" AND c.user_session_id=uid UNION SELECT
 oid, c.product_type, c.product_id, c.quantity, IFNULL(sales.price,
 c.price) FROM carts AS c INNER JOIN specific_coffees AS sc ON
 c.product_id=sc.id LEFT OUTER JOIN sales ON (sales.product_id=sc.id
 AND sales.product_type='coffee' AND ((NOW() BETWEEN
 sales.start_date AND sales.end_date) OR (NOW() > sales.start_date
 AND sales.end_date IS NULL))) WHERE c.product_type="coffee" AND
 c.user_session_id=uid;
 SELECT SUM(quantity*price_per) INTO subtotal FROM order_contents
 WHERE order_id=oid;
 UPDATE orders SET total = (subtotal + ship) WHERE id=oid;
 SELECT (subtotal + ship) INTO total;
END$$
DELIMITER ;
```

The procedure takes the customer ID, the customer's cart ID, the shipping amount, and the credit card number (the last four digits) as inbound arguments. There are two outbound arguments: **total** and **oid**. Within a **BEGIN** block, a local variable named **subtotal** is defined. Next, the record is added to the **orders** table, and the just-created ID is selected and assigned to **oid**. After that, the **order_contents** table is populated, using the INSERT...SELECT UNION SELECT query.

> Remember that variables in stored procedures do not use a dollar sign like PHP variables.

The last three lines calculate the subtotal of the order, update the **total** column in the **orders** table, and assign the total order value to the **total** variable.