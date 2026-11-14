# # Updating the Stored Procedure

The original stored procedure, as complex as its queries were, did not check for any sale prices. To do that, another JOIN must be added to each query to check the sales table. However, most items normally won't be on sale, so instead of an inner join, which only returns matches (records found in both joined tables), the queries will have to use an outer join. By adding an outer join, the query will continue to select every product currently being selected but also add in any matching rows in the sales table. In other words, an inner join is exclusive, in that it does not select any records without a corresponding match, whereas an outer join is inclusive: it also selects records that do match.

The first new query for the select_products() procedure is:

```
SELECT gc.description, gc.image, CONCAT("C", sc.id) AS sku,
CONCAT_WS(" - ", s.size, sc.caf, decaf, sc.ground_whole, sc.price) AS name,
sc.stock, sc.price, sales.price AS sale_price
FROM specific_coffees AS sc INNER JOIN sizes AS S ON s.id=sc.size_id
INNER JOIN general_coffees AS gc ON gc.id=sc.general_coffee_id
LEFT OUTER JOIN sales ON (sales.product_id=sc.id
AND sales.product_type='coffee' AND
((NOW() BETWEEN sales.start_date AND sales.end_date)
OR (NOW() > sales.start_date AND sales.end_date IS NULL)))
WHERE general_coffee_id=<some_category_id> AND stock>o
ORDER by name;
```

This query is a good example how a simple thought—allowing items to be for sale without a clear ending date—can complicate queries and logic.

This query selects specific coffee products. The first alteration (highlighted in the code) is the selection of the original price and the sale price. You'll see why the price needs to be selected again—even though it already appears in the item's name—shortly. Next, the left outer join is added on the sales table. The condition for the JOIN has three parts to it:

+   1. The sales.product_id must equal the product's ID value.

+   2. The sales.product_type value must be coffee.

+   3. The dates that the product is on sale must start before right now and end after right now, or, the sale's date must start before right now and be open-ended.

Figure 8.17 shows the results of running this query, using a category ID of 3 and without selecting the description or image (to save space). The important thing to note is that the sale_price column will have a NULL value for those products not currently on sale.