Again, there are some simple instructions, plus an indication that their data will be safe. The instructions also indicate what card types are accepted. You may choose to make this more prominent or use images to represent the accepted cards.

The form gets submitted back to billing.php.

+   5. Include the form function file:
+   
+   ```php
+   <?php include ('./includes/form_functions.inc.php'); ?>
+   ```

+   6. Create the credit card number input:
+   
+   ```html
+   <div class="field"><label for="cc_number"><strong>Card Number</strong></label><br /><?php create_form_input('cc_number', 'text', $billing_errors, 'POST', 'autocomplete="off"'); ?></div>
+   ```

The element for taking the customer's credit card number is just a text input. The potential existing value for this input can come only from POST, because the credit card number will never be stored in the session.

> ### note
> 
> You don't actually have to ask the customer what type of card they're using, because the card number is indicative of the card type.

The input uses the extra HTML autocomplete="off", which is a necessary security measure. If you don't use this attribute, and the user's browser is set to remember their form data, then the browser will record the user's credit card number in plain text on the customer's computer. That's not good. (It may still happen because of less diligent e-commerce sites, though.)

+   7. Create the expiration date elements:
+   
+   ```html
+   <div class="field"><label for="exp_date"><strong>Expiration Date</strong></label><br /><?php create_form_input('cc_exp_month', 'select', $billing_errors); ?><?php create_form_input('cc_exp_year', 'select', $billing_errors); ?></div>
+   ```

The expiration date is generated using two select menus. The first is the expiration month and the second is the year. Because the fourth argument to the create_form_input() function — for indicating where existing values come from — is not provided, the default ($ _POST) will be used.

> ### tip
> 
> The acronyms CVV, CCV, CVC, and CVVC all refer to the Card Security Code (CSC).

+   8. Create the Card Verification Value (CVV) input:
+   
+   ```html
+   <div class="field"><label for="cc_cvv"><strong>CVV</strong></label><br /><?php create_form_input('cc_cvv', 'text', $billing_errors, 'POST', 'autocomplete="off"'); ?></div>
+   ```

> ### note
> 
> Merchants are not allowed to store CVV numbers.

The CVV code is an extra security measure used to limit fraud. What the customer should enter here are three digits on the back of Visa, MasterCard, and Discover cards or the four digits on the front of American Express cards. This is an extremely sensitive piece of information, so like the card