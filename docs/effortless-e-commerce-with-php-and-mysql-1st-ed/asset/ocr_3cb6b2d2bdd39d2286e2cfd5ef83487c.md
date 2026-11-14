# 16. If the order ID and total could not be retrieved, trigger an error:

```
} else { // Could not retrieve the order ID and total.
    unset($cc_number, $cc_cvv);
    trigger_error('Your order could not be processed due to a system
    error. We apologize for the inconvenience.');
}
```

As with the checkout.php script, if the PHP code gets to the trigger_error() point, it means that the customer did everything right but the system failed. That is really one of the worst things that could happen (and really shouldn’t on a live, tested site). I’ve only included the trigger_error() call, but you should make sure that something significant—like emailing the administrator—happens in this case so that the problem gets fixed immediately. Fortunately, the customer’s contact information—name, phone number, and email address—are stored in the session, making them available to any error logging that trigger_error() does.

The error-handling function will send an email when an error occurs on a live site.

On that note, because the error-handling function, as defined, records every variable that existed at the time of the error, the customer’s credit card number and CVV value would be sent in an unsecured email or stored in a plain text log file. Such an occurrence would be a terrible security violation and a failure to abide by PCI DSS standards. To prevent this, before triggering the error, those two variables are deleted.

Think about what might happen to any customer-supplied data should an error occur at any point in the checkout process!

For these errors, you would want to also indicate to the customer what will happen next: The customer shouldn’t resubmit the order, they’ll be contacted shortly, and so forth.

# 17. If the add_order() procedure failed, trigger an error:

```
} else { // The add_order() procedure failed.
    unset($cc_number, $cc_cvv);
    trigger_error('Your order could not be processed due to a system
    error. We apologize for the inconvenience.');
}
```

This is a replication of the code in Step 16, applicable if the add_order() procedure call does not return a positive result.

# 18. Complete the form-handling conditionals:

```
} // End of isset($_SESSION['order_id']) IF-ELSE.
} // Errors occurred IF.
} // End of REQUEST_METHOD IF.
```

# 19. Save the file.

Now you can test the billing.php script as long as you purposefully create errors (because the payment-processing aspect hasn’t been defined yet).