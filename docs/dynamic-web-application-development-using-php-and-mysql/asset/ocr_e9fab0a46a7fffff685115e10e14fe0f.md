Another simple input type is ‘password’. This is similar to a text field, but when characters are typed into the field they appear on the screen as some other character, such as an asterisk:

```
<INPUT type="password" name="pword">
```

Each control can have a text label associated with it, using the LABEL element. A label must be associated with a control, or group of controls, using the ‘for’ attribute, which must match the ‘id’ attribute of a control on the form. Therefore if we want to use the LABEL tag with a form control then the control will need an ‘id’ attribute as well as a name. Here, for example, is a label for the password input type with the id ‘pword’:

```
<LABEL for="pword">Password:</LABEL>
```

This would mean the element for the password input would need to include this id:

```
<INPUT type="password" name="pword" id="pword">
```

Associating a label with a control does not affect its position in the form; you have to organize that manually. However, it does have the effect that if you click on the label in the browser, the associated control immediately gets focus.

One essential component of any HTML form is an INPUT element of type ‘submit’. This adds a button to the form that enables the form data to be sent in an HTTP request to the server. When the submit button is pressed, the ‘action’ attribute of the form is used to direct the HTTP request to the appropriate server-side resource. A form must have a ‘submit’ button in order to invoke its action, unless the HTTP request is managed by a client-side scripting language such as JavaScript, in which case the script may submit the form data.

Forms may also have a reset button, defined by an INPUT element with a type of ‘reset’. Pressing the reset button returns the components in the form to their default values, though it is debatable whether reset buttons provide any real benefit from the users’ perspective. In general, a reset button should only be used on a form if it has a useful and valid set of default values. For both submit and reset input types, the ‘value’ attribute can be used to provide a text label for the button.

Here is a very simple page with a login form that uses labels, text and password input types, and submit and reset buttons. Here we assume that there is a server-side component called ‘login’ to which the form submits its data. The form includes a table to help to organize the components into a neat layout.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
    <HEAD>
        <TITLE>Customer Login</TITLE>
    </HEAD>
    <BODY>
        <!-- File: example3-10.htm -->
        <FORM action="login" method="post">
            <TABLE>
                <TR>
                    <TD><LABEL for="loginid">Login Name:</LABEL></TD>
```