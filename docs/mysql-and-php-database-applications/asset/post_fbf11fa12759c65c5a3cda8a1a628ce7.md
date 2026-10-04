
```php
if (!empty($cart->address_id)) {
    // allow the user to create a new address
    print table_row("
        . checkbox_field("save_as_new"
```php
print end_table();

// display the available shipping methods
print subtitle("Shipping Info");

print start_table();

print table_row(
    "<b>Shipping Method</b>",
    . table_cell("<b>Per Order</b>",array("align"="right")),
    . table_cell("<b>Per Item</b>",array("align"="right")),
    . table_cell("<b>Total for This Order</b>",array("align"="right"))
);

// if no shipping method has been chosen, use the first one as a default
if (empty($cart->shipping_id)) { $cart->shipping_id = 1; }

// get the list of shipping methods from the database
$result = safe_query("select shipping_id,shipping.per_item,per_order from shipping");

while ($ship = mysql_fetch_object($result)) {
    // calculate the cost of using this method. we use a simplistic
    system: a fixed cost per order, and a per item charge.
    $shiptotal = $ship->per_order + ($cart->total_quantity * $ship->per_item);
}

// display the shipping method with a radio field allowing the
// user to choose it
```

# Chapter 14: Shopping Cart

```php
print table_row(
radio_field("shipping_id"
```

// display payment information

print subtitle("Credit Card Info");

print start_table();

if ($cart->error)
{
    // if the user tried to place an order and there was an error
    // when validating or charging the card, display it here.
    print table_row(
    table_cell("<font color=red>$cart->error</font>",array("colspan"=2))
    )
}
$cart->error = "";

// display a test card number in the form for this example.
// it has a valid format, and since we're not really trying
// to charge any cards here, AuthorizeNet will accept it.
if (empty($cart->cc_number)) {$cart->cc_number = "4912-7398-07156";};

// pick Visa as the default type, to match the default test card
if (empty($cart->cc_type_code)) {$cart->cc_type_code = "vis";}

// use the db_radio_field() function defined in
// /book/functions/forms.php
// to display the accepted credit card types as radio button fields

print table_row("<b>Credit Card:</b>",
db_radio_field("cc_type_code","cc_types","cc_type_code",
    "cc_type_code",$cart->cc_type_code)
);

print table_row("<b>Number:</b>",text_field("cc_number","$cart->cc_number,20));

// set the months array to a list of possible months
for ($i = 1; $i <= 12; $i++) { $months[$i] = $i; }

// set the years array to a list of plausible years
for ($i = 2000; $i <= 2005; $i++) { $years[$i] = $i; }

// use January 2001 as a default expiration date
if (empty($cart->cc_exp_mon)) { $cart->cc_exp_mon = 1; }
if (empty($cart->cc_exp_yr)) { $cart->cc_exp_yr = 2001; }

print table_row("<b>Expires:</b>",
    select_field("cc_exp_mon",$months,$cart->cc_exp_mon)
    .select_field("cc_exp_yr",$years,$cart->cc_exp_yr)
)
print end_table();

// save the ID of the address used in this order (if any)
print hidden_field("address_id",$cart->address_id);

// display the order button
print paragraph(submit_field("ordernow",$order_button));

print end_form();

include "end_page.php";
?>
```

# Summary

In this, the final application of the book, you've seen a few interesting things. You've learned that an application like a shopping cart requires some method of maintaining state. Probably the best way to maintain state with PHP for something like a shopping cart is with sessions.

If you wish to process credit cards, you will need a secure server, an SSL certificate, and a set of functions for processing cards. In this application we used the cURL functions for credit card processing, but there are two other function sets (PayfloPro and Cyberscash) that you should look into.

The final thing to note in this chapter is how classes were used. By extending existing classes, and writing methods to overwrite previous methods, we were able to flexibly use large blocks of code.

# Appendix A

## HTML Forms

IF YOU WANT APPLICATIONS to take user data, you are going to need a place for them to enter the information. HTML forms are easy enough to work with. There are several commonly used input types, and in browsers that use CSS to make your forms fancier. A full discussion of everything you can do with forms is beyond the scope of this book. If you need more information on forms and how they work with JavaScript, check out the documentation at microsoft.com or mozilla.org.

### Form Basics

Each form is delimited by opening and closing `<form>` tags. The `<form>` tag has the following attributes:

- action—This attribute specifies the URL of the page that form will be sent to. It can contain a relative URL (e.g., "myscript.php") or a complete URL (e.g., http://www.mydomain/myscript.php/).
- method—This attribute indicates the HTTP request type the browser will send to the server. It must be set to either GET or POST. If you set it to GET, name=value pairs will appear in the location bar. The advantage of using GET is that results can be bookmarked. The disadvantage is that variables will not be visible. The default is GET.
- name—This attribute is most useful for addressing portions of form through JavaScript.
- enctype—The default is "application/x-www-form-urlencoded", and if you are uploading files (using `<input type="file">`), should use "multipart/form-data".

A typical form will look like this:

```html
<form name="myform" action="processor.php" method="post">
```

### Input Types

Most of the work in your forms will be done by the input types. An input tag and the type attribute will determine what kind of element is rendered in your browser. Every input type must have a name attribute. To be absolutely accurate, make sure don’t forget them. As a quick example, the following would create a simple form with a single text box and a submit button. The text box has the default value of "hello there", as shown in Figure A-1.

```html
<form>
<input type="text" size="50" maxlength="15" value="hello there"><br>
<input type="submit" name="submit" value="OK">
</form>
```

![](img/245156cc77092986a3ede93c01f981_432_0.png)
Figure A-1: Simple HTML form

The input types are as follows. Note that different input types have different attributes associated with them. Each of them takes a name attribute.

- Text—This type is shown in the above example. It can take these attributes:
    - Size—which indicates the length of the box rendered in the Web browser.
    - Maxlength—which limits the number of characters that can be input into the field. Keep in mind that older browsers will ignore maxlength, and even in newer browsers, you should not rely on this attribute to limit uploads. Check your upload_max_filesize item in your .php to set the limit on the server.
    - Value—is the default value in the box. The user can override it by typing in different information.

- Password—This type is identical to the text field, except that the text that is typed into the box is shown as asterisks.

- Hidden—This type does not render on the screen. It is very useful for passing values between pages. The name and value attributes are all you need with hidden fields. Consider using hidden fields if you're uncomfortable with cookies or sessions. Note that by simply viewing the source of your Web page, a savvy user will be able to see your hidden form elements. Do not put sensitive data in hidden form.

- Submit—This places a submit button on the page. The text in the value attribute will appear on the submit button. When the form is submitted, the name and value of the submit button are passed along with all other form elements.

- Image—This type will serve the same purpose as the submit button, but it will allow you to specify an image instead of using any old ugly submit button. Treat this form element as you would any `<img>` tag. Provide both src and alt attributes.

- Reset—This type provides a button that, when pressed, alters your form to the state it was in when the page was initially loaded. The default text on the reset button is “Reset”. By adding a value attribute, you can change the text on the reset button. A Reset button does not involve PHP or the server in any way.

- File—This type gives what looks like a textbox and a button with the text “browse” on it. When hit browsers, they are given a window that allows them to go through their operating system to find the file they would like to upload. If using this input type, be sure to change the form enctype attribute to “multipart/form-data”. See Chapter 10 for a discussion of file uploads with PHP.
