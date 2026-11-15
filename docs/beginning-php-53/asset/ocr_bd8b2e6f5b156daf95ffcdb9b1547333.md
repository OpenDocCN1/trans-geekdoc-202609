![](bbox=[0.223, 0.092, 0.861, 0.447])

Figure 16-2

# ## How It Works

This script demonstrates how to use various PHP date functions, as well as some advanced features of the HTML_QuickForm PEAR package. First the script outputs the XHTML page header, linking to the common style sheet, common.css (from Chapter 2), and including some extra CSS rules to style the form.

The PHP code begins by including the two PEAR packages, then creating a new HTML_QuickForm object. This form uses the HTTP get method and sends its data back to the same script (days_old.php). The form’s $trackSubmit property is also set to true so that the script can detect when the form has been submitted:

```
require_once( "HTML/QuickForm.php" );
require_once( "HTML/QuickForm/Renderer/Tableless.php" );
$form = new HTML_QuickForm( "form", "get", "days_old.php", "", array( "style" => "width: 30em;" ), true );
```

A couple more properties of the $form object are then set. The form’s name attribute is removed, in order to make the markup XHTML-compliant, and the “* denotes required field” note is disabled, because the form only has one field (the asterisk next to the field label is hidden by the span.required CSS rule at the top of the script):

```
$form->removeAttribute( "name" );
$form->setRequiredNote( "" );
```