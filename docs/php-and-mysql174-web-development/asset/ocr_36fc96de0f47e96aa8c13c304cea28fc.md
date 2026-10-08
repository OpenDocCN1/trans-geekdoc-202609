# Creating a Sample Application: Bob's Auto Parts 13

![](bbox=[0.143, 0.115, 0.681, 0.413])

Figure 1.1 Bob's initial order form records only products and quantities

Part of the HTML for this form is shown in Listing 1.1.

# Listing 1.1 order.form.html— HTML for Bob's Basic Order Form

```
<form action="processorder.php" method="post">
<table style="border: 0px;">
<tr style="background: #cccccc; text-align: center;">Item</td>
<td style="width: 15px; text-align: center;">Quantity</td>
</tr>
<tr>
<td>Tires</td>
<td><input type="text" name="tireqty" size="3" maxlength="3" /></td>
</tr>
<tr>
<td>Oil</td>
<td><input type="text" name="oilqty" size="3" maxLength="3" /></td>
</tr>
<tr>
<td>Spark Plugs</td>
<td><input type="text" name="sparkqty" size="3" maxlength="3" /></td>
</tr>
```