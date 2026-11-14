This **UNION** query is essentially the same as that on the add inventory page, with the addition of a `WHERE table.stock > 0` clause. The thinking there is that the administrator would want to create sales only for products currently in stock.

# 17. Print each item as its own row:

```
while ($row = mysqli_fetch_array ($r, MYSQLI_ASSOC)) {
echo '<tr>
<td align="center">' . $row['category'] . ':' . $row['name'] . '</td>
<td align="center">' . $row['price'] . '</td>
<td align="center">' . $row['stock'] . '</td>
<td align="center"><input type="text" name="sale_price[' . $row['sku'] . ']" id="sale_price[' . $row['sku'] . ']" class="small" /></td>
<td align="center"><input type="text" name="start_date[' . $row['sku'] . ']" id="start_date[' . $row['sku'] . ']" class="calendar" /></td>
<td align="center"><input type="text" name="end_date[' . $row['sku'] . ']" id="end_date[' . $row['sku'] . ']" class="calendar" /></td>
</tr>';
}
```

The first three columns display values returned by the query. The last three columns each define a text input. The name of each input is an array, using the product's SKU as its index. The two date inputs have an additional `class` attribute, with a value of `calendar`. This will be used to apply the jQuery Datepicker to these inputs.

# 18. Complete the table and the form:

```
?> </tbody></table>
<div class="field"><input type="submit" value="Add These Sales"
class="button" /></div>
</fieldset>
</form>
```

# 19. Include the UI-Lightness theme CSS file and the jQuery UI library:

```
<link href="\/css\/ui-lightness\/jquery-ui-1.8.4.custom.css"
rel="stylesheet" type="text\/css" \/>
<script src="http:\/\/ajax.googleapis.com\/ajax\/libs\/jqueryui\/1.8.5\/
jquery-ui.min.js" type="text\/javascript" charset="utf-8"><\/script>
```