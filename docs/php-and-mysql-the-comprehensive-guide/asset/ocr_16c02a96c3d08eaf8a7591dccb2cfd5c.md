```
```php
$age = 0;
if ($age > 3 && $age < 18) echo "Youth";
elseif ($age >= 2 && $age <= 3) echo "Speaking age";
else echo "Small baby or adult";
```
```

# Listing 5.11 Case Differentiation in Short Form ("if__shortform.php")

**Note**

This case distinction in three lines saves a little typing work but can lead to problems later as it is quite difficult to read. When you look at your code again after a month, you will need some time to untangle the cryptic case distinctions. And the colleague who has to continue working with your code will also have trouble with this confusing variant.

# Alternative Form

With the short form, you have not yet reached the end of the alternative notations for a simple case distinction. PHP also offers a notation with a colon and `endif`:

```
```php
if (condition) :
    statements;
elseif (condition) :
    statements;
else:
    statements;
endif;
```
```

This syntax is somewhat reminiscent of Visual Basic. It is actually uncommon in PHP, but it has a practical area of application (see Figure 5.14): the simple output of HTML code. The next example shows what it looks like in practice.

```
```php
<?php
$a = 10;
if ($a < 8) :
?>

<p>if condition fulfilled</p>

<?php
elseif ($a >= 8 && $a < 20) :
?>

<p>elseif condition fulfilled</p>
```
```