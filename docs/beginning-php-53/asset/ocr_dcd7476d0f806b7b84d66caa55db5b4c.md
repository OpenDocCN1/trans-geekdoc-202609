It then creates a new HTML_QuickForm object with an empty name attribute, a method="post" attribute, an action attribute that points the form back to the script (register.php), an empty target attribute, no additional attributes, and the $trackSubmit property set to true so that the script knows when the form data has been submitted. Once the HTML_QuickForm object has been created, its empty name attribute is removed completely from the form element (this is to ensure that the page is fully XHTML 1.0 compliant:

```
$form = new HTML_QuickForm( "", "post", "register.php", "", array( "style" =>
"width: 30em;" ), true );
$form->removeAttribute( "name" );
```

Now the script calls two functions, addElements() and addRules(), that add several elements and validation rules to the $form object (you see how these work in a moment). It also calls the object's setRequiredNote() method to remove the default "** denotes required field" message; this is because the script already displays its own, similar message in the Web page:

```
addElements( $form );
addRules( $form );
$form->setRequiredNote( "" );
```

The main decision-making logic of the script follows. If the form was submitted, and it passes validation, it is processed by calling the $form object's process() method, passing in the name of the function that will handle the form data (processForm()). Then a thank-you message is displayed:

```
if ( $form->isSubmitted() && $form->validate() ) {
$form->process( "processForm" );
displayThanks();
}
```

If the form was not submitted, or it was submitted but didn't validate, the form is displayed. To do this, the script first displays the page header by calling the displayPageHeader() function in the common.inc.php file. Next, it creates a new HTML_QuickForm_Renderer_Tabless renderer object, sets the $form object's renderer to this object by calling the $form object's accept() method, and outputs the form by calling the toHtml() method of the renderer object, sending the returned markup to the browser. Finally, it outputs the page footer by calling displayPageFooter():

```
} else {
displayPageHeader( "Sign up for the book club!" );
?>
<p>Thanks for choosing to join our book club.</p>
<p>To register, please fill in your details below and click Send Details.</p>
<p>Fields marked with an asterisk (*) are required.</p>
<?php
$renderer = new HTML_QuickForm_Renderer_Tabless();
$form->accept( $renderer );
echo $renderer->toHtml();
displayPageFooter();
}
```

Next comes the addElements() function to add the various form fields and controls to the $form object. If you've read the previous few sections, most of this code should be self-explanatory. A couple of the controls warrant special attention though. The two gender radio buttons are created with empty