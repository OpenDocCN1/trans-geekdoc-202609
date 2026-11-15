Now to the superglobal arrays: `$_REQUEST` contains all form data (and also cookies; see Chapter 14), regardless of whether you use GET or POST. It makes more sense to access the `$_POST` and `$_GET` special arrays for POST and GET data, respectively.

Where the form is sent to is specified (for GET and POST) in the action attribute of the `<form>` tag. With GET, the form data is also automatically appended to this address. However, most PHP scripts look like this: both the form itself and the PHP code that evaluates the form data are in the same file. One of the advantages of this is that everything is clearly arranged in one place. In many tutorials you will now find the advice to equip the form—in this case, as follows:

```
<form action="<?php echo $PHP_SELF; ?>">
```

The `$PHP_SELF` variable contains the URL of the current script. This is configuration-dependent—but what always works is `$_SERVER["PHP_SELF"]`. But this is usually not necessary. What happens if action has not been set? Let's look at the W3C HTML specification. At `http://s-prs.co/v602217`, it says that for HTML 4 that the behavior of the browser is undefined if the attribute is not set; in the DTD of (X)HTML, action is marked as a mandatory attribute (#REQUIRED). However, this restriction no longer exists in HTML5. Using action="" is still good style.

In practice, however, things look different. If a web browser does not find an action attribute, it automatically sends the current form to the current script, which is exactly what we want to do here. Although this is not specified anywhere, it is implemented by all relevant browsers. But even this is dangerous:

```
<form action="<?php echo $_SERVER["PHP_SELF"]; ?>">
```

The reason is that under certain circumstances, `$_SERVER["PHP_SELF"]` contains the complete path to the current script, including any URL appendices. However, an attacker would then be able to append malicious JavaScript code to the address—with dangerous consequences (you can find out more about various security issues in Chapter 32). You therefore must first remove special characters (such as double quotation marks and angle brackets) from the output. This can be done with the `htmlspecialchars()` function, which will be used more frequently later:

```
<form action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
```

Ahead, we add code to the form step by step in order to output the data entered. We proceed according to the form field type. This has the advantage that you can end up working not only with the example form, but with any form; the form field types are always the same.

First, two important notes:

+   As form input may also contain HTML special characters, all output is first converted to HTML using `htmlspecialchars()` beforehand.