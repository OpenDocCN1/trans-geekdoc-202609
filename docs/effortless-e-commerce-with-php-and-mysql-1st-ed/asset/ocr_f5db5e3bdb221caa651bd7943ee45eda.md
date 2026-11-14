The registration script I came up with, which you can download from www.DMCInsights.com/ecom/, is about 160 lines total, including comments. Rather than walk you through the entire script in one long series of steps, let’s look at this script as its three distinct parts.

# # Creating the Basic Shell

Every PHP page in the site—every script that a user will access directly and that won’t be included by other PHP scripts—has the same basic structure. First, it includes the configuration file, then the HTML header (likely setting the page title beforehand), and then the MySQL connection script. Next comes the page-specific content and, finally, the footer is included. Here then, is what you can start with for `register.php`:

# ## register.php

```
```php
<?php
require ('./includes/config.inc.php');
$page_title = 'Register';
include ('./includes/header.html');
require (MYSQL);
?>
<h3>Register</h3>
<p>Access to the site's content is available to registered users at a cost
of $10.00 (US) per year. Use the form below to begin the registration
process. <strong>Note: All fields are required.</strong> After
completing this form, you'll be presented with the opportunity to
securely pay for your yearly subscription via <a href="http://www.
paypal.com">PayPal</a></p>
<?php
include ('./includes/footer.html');
?>
```
```

For the registration page, it’s important that you give the customer a sense of the process. You may want to graphically indicate the steps involved using a progress bar (or progress meter), although this particular process really only has two steps. Also indicate how all the data will be used (for example, explain that they won’t be spammed), and maybe refer them to whatever site policies exist (I’ve created a link to a policy file in the footer). Just do everything you can to reassure the user that it’s safe to proceed.