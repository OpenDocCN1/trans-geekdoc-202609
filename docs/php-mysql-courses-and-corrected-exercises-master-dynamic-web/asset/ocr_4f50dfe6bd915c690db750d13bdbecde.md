Server-side anti-CSRF token validation: When the form is submitted, the anti-CSRF token is also submitted along with the form data. The code checks whether the submitted token matches the token stored in the session. If the two tokens match, the request is legitimate and can be processed successfully. Otherwise, an invalid CSRF error is displayed.

This anti-CSRF token mechanism ensures that each request submitted from the form contains a unique and valid token, preventing CSRF attacks by verifying that the request actually comes from the authorized website.

To illustrate the generation and validation of an anti-CSRF token in PHP, we're going to create two files in the ebookphp directory: the file named form_csrf.php, which contains a form, and the file named csrf_processing.php, which will process the data submitted by this form. Here's a simple example of the code for these two files:

# File 1: form_csrf.php :

```
<?php
session_start();

// Generate anti-CSRF token
if (!isset($_SESSION['csrf_token'])) {
    $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
}
```