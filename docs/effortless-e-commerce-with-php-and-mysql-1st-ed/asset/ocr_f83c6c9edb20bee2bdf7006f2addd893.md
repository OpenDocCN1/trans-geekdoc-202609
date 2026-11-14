Now that you (hopefully) understand how the **SELECT** query works, consider that the **SELECT** query can be used immediately as the values for an **INSERT** query, thanks to the **INSERT...SELECT** construct. The **INSERT** for `order_contents` is:

```
INSERT INTO order_contents (order_id, product_type, product_id, quantity,
price_per) VALUES (...)
```

Putting together the INSERT and SELECT queries, the entire query becomes:

```
INSERT INTO order_contents (order_id, product_type, product_id, quantity,
price_per)
SELECT oid, c.product_type, c.product_id, c.quantity,
IFNULL(sales.price, ncp.price)
FROM carts AS c
INNER JOIN non_coffee_products AS ncp ON c.product_id=ncp.id
LEFT OUTER JOIN sales ON (sales.product_id=ncp.id AND
sales.product_type='other' AND
((NOW() BETWEEN sales.start_date AND sales.end_date) OR (NOW() >
sales.start_date AND sales.end_date IS NULL))) 
WHERE c.product_type="other" AND c.user_session_id=<user_cart_id>
UNION
SELECT oid,...
```

By adding the selection of the `oid` variable, that value can be inserted into `order_contents` at the same time.

Moving on in the procedure, the last step is to update the **orders** table for the order total. The total can be determined by running an aggregating query on `order_contents` for the current order:

```
SELECT SUM(quantity*price_per) INTO subtotal FROM order_contents
WHERE order_id=oid;
```

And now the orders table can be updated:

```
UPDATE orders SET total = (subtotal + ship) WHERE id=oid;
```

Finally, the order total will be necessary outside of the procedure (as part of the payment processing). To make that possible, the total should also be assigned to an outbound argument:

```
SELECT (subtotal + ship) INTO total;
```