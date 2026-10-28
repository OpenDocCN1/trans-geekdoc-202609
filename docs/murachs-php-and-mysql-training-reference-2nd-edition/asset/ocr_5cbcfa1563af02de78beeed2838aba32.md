# The admin/product/product_view.php file

```
```php
<?php include '../../view/header.php'; ?>
<?php include '../../view/sidebar_admin.php'; ?>

<section>
    <h1>Product Manager - View Product</h1>

    <!-- display product -->
    <?php include '../../view/product.php'; ?>

    <!-- display buttons -->
    <div class="last_paragraph">
        <form action="." method="post" id="edit_button_form">
            <input type="hidden" name="action" value="show_add_edit_form"/>
            <input type="hidden" name="product_id"
                   value="<?php echo $product['productID']; ?>" />
            <input type="hidden" name="category_id"
                   value="<?php echo $product['categoryID']; ?>" />
            <input type="submit" value="Edit Product" />
        </form>
        <form action="." method="post" >
            <input type="hidden" name="action" value="delete_product"/>
            <input type="hidden" name="product_id"
                   value="<?php echo $product['productID']; ?>" />
            <input type="hidden" name="category_id"
                   value="<?php echo $product['categoryID']; ?>" />
            <input type="submit" value="Delete Product" />
        </form>
    </div>
</section>
<?php include '../../view/footer.php';
```
```

# The admin/product/product_add_edit.php file

```
```php
<?php include '../../view/header.php'; ?>
<?php include '../../view/sidebar_admin.php'; ?>
<?php
if (isset($product_id)) {
    $heading_text = 'Edit Product';
} else {
    $heading_text = 'Add Product';
}
?>

<section>
    <h1>Product Manager - <?php echo $heading_text; ?></h1>
    <form action="index.php" method="post" id="add_edit_product_form">
        <?php if (isset($product_id)) { ?>
            <input type="hidden" name="action" value="update_product" />
            <input type="hidden" name="product_id"
                   value="<?php echo $product_id; ?>" />
        <?php else: ?>
            <input type="hidden" name="action" value="add_product" />
        <?php endif; ?>
        <input type="hidden" name="category_id"
               value="<?php echo $product['categoryID']; ?>" />
```
```

Figure 20-5 — The Product Manager application (part 4 of 5)