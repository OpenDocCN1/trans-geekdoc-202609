OOH Forms is an independent class and does not need any other classes from PHPlib. To include this OOH Forms class, simply update the include_path statement in the php.ini file to point to the php distribution directory in the unpacked PHPlib distribution.

There are five files in the OOH Forms library: oohforms.inc, of_checkbox.inc, of_radio.inc, of_select.inc, of_text.inc, and of_textarea.inc. Including oohforms.inc automatically includes the others. You can opt to manually include the files for just the form elements you use in oohforms.inc, or you may wish to cut and paste the contents of the element files into oohforms.inc to save the overhead of multiple includes; however, for most purposes oohforms.inc will suffice.

A typical OOH Forms script can be divided in three sections:

+   Creating an instance of the form and defining form elements

+   Checking if the script/form was submitted, and then validating and processing the data

+   Rendering the form and associated JavaScript for the browser

# Sample Application

Rather than having a tutorial about OOH Forms we will look at a script illustrating its power. Let's start by building a simple HTML form for a jobs web site to achieve the following:

+   The person filling out the form must input their name. The name can not be less than 4 characters long or contain numbers.

+   This person must also input an e-mail address which is syntactically correct.

+   At least one city must be chosen as preferred. Users come to the site to register their interest in switching jobs. As such, they need to specify which cities they are prepared to move to.

To use OOH Forms in the code, include the necessary file:

```
<?php
include("oohforms.inc");
```

Then create an instance of OOH Forms:

```
$f = new form;
```

Next, elements are added to the form. To add elements, the OOH add_element() method has to be used:

```
// Full Name
$f->add_element(array("name">="name",
"type">="text",
"size">="20",
"minlength">=">4",
"length_e">=">"You must type your name and it should be
at least 4 characters long",
"valid_e">=">"Your name cannot have numerals.",
"valid_regex">=">"^([a-zA-Z ])*$" ));
```