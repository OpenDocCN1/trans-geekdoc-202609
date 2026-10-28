# The Add Item view

Figure 12-12 shows the code for the Add Item page. This page displays
a form that lets the user add an item to the cart by selecting a product and a
quantity for that item. In addition, this page displays a link that lets the user view
the cart without adding an item.

The form uses the POST method to submit the data back to the index.php
controller for processing. This form includes a hidden field with a name of
“action” and a value of “add” to indicate that the controller should add the item
to the cart.

The first <select> tag has a name of “productkey”. This tag lets the user
select a product from a drop-down list. Within this tag, the PHP code uses a
foreach loop to generate the <option> tags for the drop-down list. To start, this
code loops through each item in the products array. At the beginning of the loop,
this code formats the cost of each item as a number with two digits, and it uses
the item name and formatted cost to generate the text to display for the item.

Within the loop, this code sets the value of the <option> tag to the key for
the product. As a result, the key for the selected product is submitted to the
controller. This code sets the text for the <option> tag to a string that includes
the name and cost of the product, so this text is displayed in the drop-down list.

The second <select> tag has a name of “itemqty”. This tag lets the user
select the quantity from a drop-down list. This code uses a for loop to generate
the <option> tags for the drop-down list. These tags display values from 1 to 10.
Here, the code uses the index of the loop as both the value that’s submitted to the
control and the text that’s displayed in the drop-down list.

At the end of the page, the View Cart link lets the user go to the Cart view
page without adding an item. Here, the href attribute of the <a> tag links to
the controller and submits an action parameter of show_cart. As a result, this
parameter is passed to the controller as part of a GET request. That’s why the
controller checks both POST and GET requests for the action to perform.