indeed live in the United States, you’ve saved the customer some typing. And if the customer doesn’t live in the U.S., he or she can just replace **US** with the appropriate country. Also, if the program automatically enters **US** as the value in the field, you know that the information doesn’t have any errors in it.

To display a text field that contains information, you use the following format for the input field HTML statements:

```
```html
<input type="text" name="country" value="US">
```
```

By using PHP, you can use a variable to display this information with either of the following statements:

```
```php
<input type="text" name="country"
       value="<?php echo $country ?>">
echo "<input type='text' name='country' value='$country'>";
```
```

The first example creates an input field in an HTML section, using a short PHP section for the value only. The second example creates an input field by using an **echo** statement inside a PHP section. If you’re using a long form with only an occasional variable, using the first format is more efficient. If your form uses many variables, it’s more efficient to use the second format.

If you have user information stored in a database, you might want to display the information from the database in the form fields. For instance, you might show the information to the user so that he or she can make any needed changes. Or you might display the shipping address for the customer’s last online order so that he or she doesn’t need to retype the address. Listing 8-7 shows the program `displayAddress.php`, which displays a form with information from the database. This form is very similar to the form shown in Figure 8-5 except that this form has information in it (retrieved from the database) and the fields in the form in Figure 8-5 are blank.

![](bbox=[0.071, 0.631, 0.162, 0.703])

# ## Registering long arrays

A new `php.ini` setting introduced in PHP 5 allows you to prevent the older, long arrays from being created automatically by PHP. It’s very unlikely that you will need to use them unless you’re using some old scripts containing the long variables. The following line in `php.ini` controls this setting:

```
```ini
register_long_arrays = On
```
```

At the current time, this setting is **On** by default. Unless you’re running old scripts that need the

old arrays, you should change the setting to **Off** so that PHP doesn’t do this extra work. Although the setting is currently **On** by default, that could change. The default setting might change to **Off** in a future version. If you’re using some old scripts and are getting errors on lines containing the long arrays, such as `$HTTP_GET_VARS`, check your `php.ini` setting for long arrays. It might be **Off**, and the long arrays needed by the older script are not being created at all.