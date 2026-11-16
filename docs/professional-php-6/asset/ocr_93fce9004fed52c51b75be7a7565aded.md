This holds equally true for non-user modifiable controls — labels, for example. If the value (that is, content) of a label is modified either in the servlet itself or in a foreign servlet (as is perfectly permissible), then that value is retained for the remainder of that user's session.

During application development, you may find this frustrating from time to time. You may want to “reset” a page to its natural state, and not have your test input cluttering up text boxes. What’s the easiest way to do this? Simply flush your browser’s cookies. Your session will be lost, a new one generated, and the page reset to its “natural” state.

# Validation

A few checks are performed on user input during the signup process. The only non-optional field is an e-mail address; first and last name are considered optional. For that reason, all checks relate to the e-mail address field — is it present, is it valid, and, most important of all, has it already been submitted?

Only if all three checks are passed will the user’s input be saved. Otherwise, the user is admonished suitably and asked to correct it.

The first thing you’ll notice is that the value of the user input isn’t retrieved using $_POST. Instead, Ulysses gives you access to a foreign servlet’s controls, as shown here:

```
$objServlet = Servlet::GetReferringServlet();
$strFN = $objServlet->objFirstName->GetValue();
$strLN = $objServlet->objLastName->GetValue();
$strEM = $objServlet->objEMail->GetValue();
```

This is useful, because there may well be times when you don’t want raw POST data. Since you can access any method the page control exposes, you are not just limited to GetValue(). Indeed, that method can be overloaded, meaning the manner in which its value is returned can be refined within the control class itself — and not within your servlet.

Ulysses does not provide any special validation routines. You can either roll your own or use one of the many available PEAR classes to do the trick. In this case, the validation is so simple that native PHP code is used to check that the e-mail address is valid, that it has been provided, and that it is not already in the database.

Should any of those checks fail, an exception is thrown. When it is caught, the status label of the original servlet is set to an error message passed to the exception. Its redirectTo() method is then invoked, which throws the user back to the home page:

```
} catch (Exception $e) {
    $objServlet->objStatusLabel->SetCaption($e->getMessage()));
    $objServlet->redirectTo();
};
```

When the home page reloads, the updated status label indicates to the user that there is a problem, and the user is invited to correct the submission.