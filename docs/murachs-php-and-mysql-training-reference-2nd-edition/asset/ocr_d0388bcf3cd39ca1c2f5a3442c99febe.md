# The index.php file (continued)

```
```php
case 'show_add_item':
    include('add_item_view.php');
    break;
case 'empty_cart':
    unset($_SESSION['cart13']);
    include('cart_view.php');
    break;
}
?>
The cart_view.php file
<!DOCTYPE html>
<html>
<head>
    <title>My Guitar Shop</title>
    <link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>
    <header>
        <h1>My Guitar Shop</h1>
    </header>
    <main>
        <h1>Your Cart</h1>
        <?php if (empty($_SESSION['cart13']) ||
                  count($_SESSION['cart13']) == 0) : ?>
            <p>There are no items in your cart.</p>
        <?php else: ?>
            <form action="." method="post">
                <input type="hidden" name="action" value="update">
                <table>
                    <tr id="cart_header">
                        <th class="left">
                            Item
                            <input type="radio"
                            <?php if ($sort_key == 'name') : ?>
                                checked
                            <?php endif; ?>
                            name="sortkey" value="name"></th>
                        <th class="right">
                            <input type="radio"
                            <?php if ($sort_key == 'cost') : ?>
                                checked
                            <?php endif; ?>
                            name="sortkey" value="cost">
                            Item Cost</th>
                        <th class="right">
                            <input type="radio"
                            <?php if ($sort_key == 'qty') : ?>
                                checked
                            <?php endif; ?>
                            name="sortkey" value="qty">
                            Quantity</th>
```
```