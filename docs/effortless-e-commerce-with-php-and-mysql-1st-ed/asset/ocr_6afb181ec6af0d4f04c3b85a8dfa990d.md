# 8. Create the last name, addresses, and city inputs:

```
`<div class="field"><label for="last_name"><strong>Last Name
<span class="required">*</span></strong></label><br /><?php
create_form_input('last_name', 'text', $shipping_errors); ?>< /div>
<div class="field"><label for="address1"><strong>Street Address
<span class="required">*</span></strong></label><br /><?php
create_form_input('address1', 'text', $shipping_errors); ?>< /div>
<div class="field"><label for="address2"><strong>Street Address,
Continued</strong></label><br /><?php create_form_input(
'address2', 'text', $shipping_errors); ?>< /div>
<div class="field"><label for="city"><strong>City
<span class="required">*</span></strong></label><br />
<?php create_form_input('city', 'text', $shipping_errors); ?>< /div>`
```

These four inputs are repetitions of the first name input, except that the second address field is not required.

# 9. Create the state select menu:

```
`<div class="field"><label for="state"><strong>State
<span class="required">*</span></strong></label><br />
<?php create_form_input('state', 'select', $shipping_errors); ?>< /div>`
```

To create the select menu using the create_form_input() function, the second argument just needs to be select. The data used in the menu is based upon the element's name.

# 10. Create the zip code, phone number, and email address inputs:

```
`<div class="field"><label for="zip"><strong>Zip Code
<span class="required">*</span></strong></label><br />
<?php create_form_input('zip', 'text', $shipping_errors); ?>< /div>
<div class="field"><label for="phone"><strong>Phone Number
<span class="required">*</span></strong></label><br />
<?php create_form_input('phone', 'text', $shipping_errors); ?>< /div>
<div class="field"><label for="email"><strong>Email Address
<span class="required">*</span></strong></label><br />
<?php create_form_input('email', 'text', $shipping_errors); ?>< /div>`
```

# 11. Complete the form:

```
`<br clear="all" />
<div align="center"><input type="submit" value="Continue onto Billing" class="button" /></fieldset></form></div>`
```

As mentioned earlier, this button, which continues the checkout process, needs to be impossible to miss.