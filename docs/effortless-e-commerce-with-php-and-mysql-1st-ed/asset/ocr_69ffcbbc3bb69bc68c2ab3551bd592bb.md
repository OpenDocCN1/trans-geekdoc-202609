# 9. Create the table:

```
echo '<table border="0" width="100%" cellspacing="2"
cellpadding="2">
<thead>
<tr>
<th align="center">Item</th>
<th align="right">Price Paid</th>
<th align="center">Quantity in Stock</th>
<th align="center">Quantity Ordered</th>
<th align="center">Ship?</th>
</tr>
</thead>
<tbody>';
```

The table lists the ordered items, along with the price paid, the quantity
currently in stock, the quantity ordered, and when the item has shipped,
if applicable.

# 10. Create a flag variable to track if the order has already shipped:

```
$shipped = true;
```

The administrator is going to be given the option of processing the pay-
ment for this order only if it hasn't already shipped. The assumption will
be that it has, and later code will change this setting if that's not the case.

# 11. Print each item:

```
do {
echo '<tr>'
<th align="left">'. $row['item']. '</th>
<th align="right">'. $row['price_per']. '</th>
<th align="center">'. $row['stock']. '</th>
<th align="center">'. $row['quantity']. '</th>
<th align="center">'. $row['sd']. '</td>
</tr>';
```

Because one row has already been fetched, the less common do...while
loop will be used to navigate the remaining query results. This construct
performs some actions first and checks the conditional last, thereby guar-
anteeing that the code within the loop will be executed at least one time.
Within the loop, each value is displayed within a table row.

# 12. Update the shipping status:

```
if (!$row['sd']) $shipped = false;
```