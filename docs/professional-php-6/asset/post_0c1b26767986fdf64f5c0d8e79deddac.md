
![](img/a1b732997d9cb194dceec0570dc79710_377_0.png)

Figure 14-1 Sample newsletter signup page

If you look again at the servlet, it should be reasonably easy to figure out what's going on behind the scenes:

```
$this->objTitle = new Title("Email Bulletin Signup", "default");
$this->objFirstName = new TextBox("firstname");
$this->objLastName = new TextBox("lastname");
$this->objEmail = new TextBox("email");
$this->objStatusLabel = new Label("status");
$this->objSuccessLabel = new Label("success");
$this->objFirstNameLabel = new Label("firstnameLabel", "First Name");
$this->objLastNameLabel = new Label("lastnameLabel", "Last Name");
$this->objEmailLabel = new Label("emaillabel", "Email Address *");
```

Each of these lines represents the declaration of a control on the page. The syntax for declaring a title control (which emulates an HTML title tag) is simple — title text first, followed by an identifier:

```
$this->objTitle = new Title("Email Bulletin Signup", "default");
```

The corresponding entry in the template is simple, too:

```
<tpl:title id="default" />
```

The Ulysses framework, when parsing the template, will look for an instance of the Title class declared in the corresponding servlet, extract its textual value, and render the necessary HTML title tag:

```
<title>Email Bulletin Signup</title>
```

Other controls work in a similar fashion. Labels and text boxes are declared in this example. Notice how labels do not necessarily have to have an initial value — which is useful if you are using labels to (maybe) display error messages on a conditional basis. The status label and success label work exactly this way — and conditional syntax in the template ensures they are only displayed if they are nonblank:

```
<tpl:if $status neq "">
    <p class="errorText">
    <tpl:label id="status" />
    </p>
</tpl:if>
```

This template syntax may look familiar to you. Indeed, it should — it's just the Smarty template engine in disguise, something you met earlier in this book.

## Processing User Input

Should you try to submit the data capture form as it stands, you'll meet a 404 error — for the simple reason that the target of the form does not exist. Review the template:

```
<form method="post" action="/Signup">
```

As you can see, the form is attempting to post to /Signup, which implies that a servlet called SignupServlet must be created, and its __doPost() method populated.

This servlet serves two functions: validating user input and, if it passes, saving the entry into the database. It only has one ultimate course of action: passing control back to the original submitting servlet. In so doing, it can "talk" to the servlet it is about to pass control back to, setting values of page controls such as labels and text boxes.

The following code comprises signupservlet.php in php/servlets. There's no corresponding template, as this servlet has no GET method:

```php
<?
class SignupServlet Extends Servlet {
    public function __construct($objSmarty, $objSession, $queryStringParms,
        $strPageIdentifier) {
    }
    public function __doGet($objSmarty, $objSession, $queryStringParms) {
        header("Location: /Home");
        exit(0);
    }
    public function __doPost($objSmarty, $objSession, $queryStringParms) {
        $objServlet = Servlet::GetReferringServlet();
    }
    # Validate
    $strFN = $objServlet->objFirstName->GetValue();
    $strLN = $objServlet->objLastName->GetValue();
    $strEM = $objServlet->objEmail->GetValue();

    $objServlet->objEmailLabel->strCSSClass = "";

    if (strlen($strEM) < 1) {
        $objServlet->objEmailLabel->strCSSClass = "erroneous";
    };

    try {
        if (strlen($strEM) < 1) {
            throw new Exception("Sorry, you didn't fill in all
            required fields. Please try again.");
        };
        if (Subscriber::checkExists($strEM) == true) {
            $objServlet->objEmailLabel->strCSSClass = "erroneous";
            throw new Exception("Sorry, a subscriber by this
            address already exists. Please try again.");
        };
        if (preg_match('/^[a-z0-9!#$%&*+==?^_`{|}~-]+(\.[a-z0-9!#$%&*+==?^_`{|}~-]+)*@([a-z0-9]+.)+[a-z]{2,6})$/ix', $strEM) <= 0) {
            $objServlet->objEmailLabel->strCSSClass = "erroneous";
            throw new Exception("Sorry, that email address isn't
            valid. Please try again.");
        };
    } catch (Exception $e) {
        $objServlet->objStatusLabel->SetCaption($e->getMessage());
        $objServlet->redirectTo();
    };

    # TODO - Save here

}
?>
```

You'll notice there's a TODO here. If all validation is successful, you want to save the record to the database. You'll fill that bit in shortly. For now, it's omitted for clarity.

### Persistence

The first thing you'll notice is that there's no explicit code to handle the persistence of user input controls such as text boxes. Great news — it's not needed. The Ulysses framework takes care of it for you. As soon as you submit a page, its entire contents (or state) is captured and held in the session. If the user returns to that page for any reason, the form will appear in exactly the state it was submitted.

This holds equally true for non-user modifiable controls — labels, for example. If the value (that is, content) of a label is modified either in the servlet itself or in a foreign servlet (as is perfectly permissible), then that value is retained for the remainder of that user's session.

During application development, you may find this frustrating from time to time. You may want to “reset” a page to its natural state, and not have your test input cluttering up text boxes. What’s the easiest way to do this? Simply flush your browser’s cookies. Your session will be lost, a new one generated, and the page reset to its “natural” state.

### Validation

A few checks are performed on user input during the signup process. The only non-optional field is an e-mail address; first and last name are considered optional. For that reason, all checks relate to the e-mail address field — is it present, is it valid, and, most important of all, has it already been submitted?

Only if all three checks are passed will the user’s input be saved. Otherwise, the user is admonished suitably and asked to correct it.

The first thing you’ll notice is that the value of the user input isn’t retrieved using $_POST. Instead, Ulysses gives you access to a foreign servlet’s controls, as shown here:

```
$objServlet = Servlet::GetReferringServlet();
$strFN = $objServlet->objFirstName->GetValue();
$strLN = $objServlet->objLastName->GetValue();
$strEM = $objServlet->objEmail->GetValue();
```

This is useful, because there may well be times when you don’t want raw POST data. Since you can access any method the page control exposes, you are not just limited to GetValue(). Indeed, that method can be overloaded, meaning the manner in which its value is returned can be refined within the control class itself — and not within your servlet.

Ulysses does not provide any special validation routines. You can either roll your own or use one of the many available PEAR classes to do the trick. In this case, the validation is so simple that native PHP code is used to check that the e-mail address is valid, that it has been provided, and that it is not already in the database.

Should any of those checks fail, an exception is thrown. When it is caught, the status label of the original servlet is set to an error message passed to the exception. Its redirectTo() method is then invoked, which throws the user back to the home page:

```
} catch (Exception $e) {
    $objServlet->objStatusLabel->SetCaption($e->getMessage());
    $objServlet->redirectTo();
};
```

When the home page reloads, the updated status label indicates to the user that there is a problem, and the user is invited to correct the submission.

Notice how CSS classes are used to highlight incorrectly filled fields:

```
`$objServlet->objEmailLabel->strCSSClass = "erroneous";`
```

This enables the e-mail address label to be highlighted in red, which shows the user at a glance where the error lies.

### A Quick Check

Before proceeding any further, prove to yourself that the code works by attempting to submit the form with an empty e-mail address field. You should see something similar to Figure 14-2.

![](img/a1b732997d9cb194dceec0570dc79710_381_0.png)

Figure 14-2 Result of submitting a form without an e-mail address

When viewed on your screen, the “Email Address” field is highlighted in red, and a message admonishing the user is presented.

Click Refresh in your browser, and you’ll see that the page state is still retained — and, importantly, there’s no resubmission of the form.

### Saving Input

Remember the earlier block of servlet code where you saw a comment saying `TODO`? That was where you were going to save the subscriber if the submission was successful (that is, all validation checks were passed).
