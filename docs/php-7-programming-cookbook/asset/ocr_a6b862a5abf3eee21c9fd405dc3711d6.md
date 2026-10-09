9. Next we wrap the purchases table inside an initially invisible <div> tag. Then, we can place a limit of how many sub-rows are initially visible, and add a link that reveals the remaining purchase data:

```
```
<div class="row" id="<?='purchase' . $key ?>"
style="display:none;">
<table>
<tr>
<th>Transaction</th><th>Date</th><th>Qty</th>
<th>Price</th><th>Product</th>
</tr>
<?php $count = 0; ?>
<?php $first = TRUE; ?>
<?php foreach ($data['purchases'] as $purchase) : ?>
<?php if ($count > SALROWS_PER_PAGE && $first) : ?>
<?php $first = FALSE; ?>
<?php $subId = 'subrow' . $key; ?>
</table>
<a href="#" onClick="showOrHide('<?=' $subId ?>')">More</a>
<div id="<?=' $subId ?>" style="display:none;">
<table>
<?php endif; ?>
<?php $class = ($count++ & 01) ? 'color1' : 'color2'; ?>
<tr>
<td class="<?= $class ?>"><<?= $purchase['transaction'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['date'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['quantity'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['sale_price'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['title'] ?>></td>
</tr>
<?php endforeach; ?>
</table>
<?php if (!$first) : ?></div><?php endif; ?>
</div>
```
```

10. We then add a button that, when clicked, reveals the hidden <div> tag:

```
```
<input type="button" value="Purchase" class="buttonRight"
onClick="showOrHide('<?=' 'purchase' . $key ?>')">
```
```

# How it works...

Place the code described in steps 1 to 5 into a file, chap_10_html_table_multi_array_hidden.php.

Just inside the while() loop, add the following:

```
```
printf('%6s : %20s : %8s : %20s', PHP_EOL,
$row['id'], $row['name'], $row['transaction'], $row['title']);
```
```