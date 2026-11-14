
## 14. Begin the form:

```
<h3>Create Sales</h3>
<p>To mark an item as being on sale, indicate the sale price, the date
the sale starts, and the date the sale ends. You may leave the end date
blank, thereby creating an open-ended sale. Only the currently
stocked products are listed below!</p>
<form action="create_sales.php" method="post"
accept-charset="utf-8">
<fieldset>
```

This form begins with some instructions, because the use of the dates could be confusing.

## 15. Begin a table:

```
<table border="0" width="100%" cellspacing="2" cellpadding="2">
<thead>
<tr>
<th align="right">Item</th>
<th align="right">Normal Price</th>
<th align="right">Quantity in Stock</th>
<th align="center">Sale Price</th>
<th align="right">Start Date</th>
<th align="right">End Date</th>
</tr>
</thead>
<tbody>
```

## 16. Retrieve every product that's currently in stock:

```
<?php
$q = 'SELECT CONCAT("O", ncp.id) AS sku, ncc.category, ncp.name,
ncp.price, ncp.stock FROM non_coffee_products AS ncp INNER JOIN
non_coffee_categories AS ncc ON ncc.id=ncp.non_coffee_category_id
WHERE ncp.stock > 0 ORDER BY category, name) UNION (SELECT
CONCAT("C", sc.id), gc.category, CONCAT_WS(" - ", s.size,
sc.caf_decaf, sc.ground_whole), sc.price, sc.stock FROM
specific_coffees AS sc INNER JOIN sizes AS s ON s.id=sc.size_id
INNER JOIN general_coffees AS gc ON gc.id=sc.general_coffee_id
WHERE sc.stock > 0 ORDER BY sc.general_coffee_id, sc.size,
sc.caf_decaf, sc.ground_whole)';
$r = mysqli_query ($dbc, $q);
```

This **UNION** query is essentially the same as that on the add inventory page, with the addition of a `WHERE table.stock > 0` clause. The code of 1, indicating
a successful request of the payment gateway, will be returned.

The orders are listed starting with the newest.

- 5. Print each record in the table:

```
while ($row = mysqli_fetch_array ($r, MYSQLI_ASSOC)) {
echo '<tr>
<td align="center"><a href="view_order.php?oid=' . $row['id'] . '">' . $row['id'] . '</a></td>
<td align="center">$' . $row['total'] . '</td>
```
