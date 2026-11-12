Hello, Alice Dupont! You're back.

# Modifying and Deleting Cookies

To modify an existing cookie, you can simply create a new cookie with the same name as the one you wish to modify. This will overwrite the old cookie with the new values specified. Just make sure you specify the same options as the original cookie, such as path and validity time, to avoid any inconsistencies.

If, for example, you wish to modify the "user" cookie previously created, you can proceed as follows:

```
<?php
setcookie('user', 'theme_fonce', time() + 72000, '/');
?>
```

This code modifies the existing user cookie by replacing its value with "theme_fonce". The modified cookie will be valid for 72,000 seconds (20 hours) from the moment it is executed, and will be accessible from the