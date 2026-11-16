
```php
$form->setStyle(new ExtraNetStyle());
$form->display();
```

If we wanted to change the colours to something a bit different, we would just have to change the line of code as shown below:

```php
$form->setStyle(new NewStyle());
$form->display();
```

and we will not have to change any of the form engine's logic.

The second last piece of code to output the form engine is a data validation object. We already built one when we were talking about delegation. The object model for this is shown below:

![](img/9cf7789dba9b16ef3f8576d5aea89186_174_0.png)

To manage multiple forms, we'll need the actual FormEngine object, which is our last object. This FormEngine will be our tool to manage multiple forms and will be the guide to reproduce the JavaScript library code when using multiple forms. This object also acts as a factory class since we can create forms through it. Here is the object model:

![](img/9cf7789dba9b16ef3f8576d5aea89186_174_1.png)

The reason why we have the FormEngine object create forms is that it can tabulate the details that are needed for the JavaScript code. This is so we can have multiple forms with client-side data validation. That nearly completes our form. Here is some sample code showing how easy it is to construct the form that was displayed earlier:

```php
$formEngine = new FormEngine();
$form = $formEngine->create("form", "Form Name", $PHP_SELF, "post");
$form->addElement(new FormHeader('General Information'));
$form->addElement(new TextField('name', '', 'Name', ALPHA,
"You have failed to enter your name", true));

$form->addElement(new HiddenField('userID', '1'));

$form->addElement(new PasswordField('password', '', 'Password',
PASSWORD,
"You have failed to choose a password larger than 4 characters",
true));

$form->addElement(new TextField('email', '', 'Email Address', EMAIL,
"You have entered your email address incorrectly", true));

$form->addElement(
new TextArea('description', '', 'Description', ALPHANUMERIC,
"You have failed to enter any description about yourself",
false, array("rows" => 10, "cols" => 40,)));

$form->addElement(new DateField('startdate', '', 'Start Date',
false));

$form->addElement(new FileBrowser('file', 'File', false));

$combo = new ComboBox('wagetype', 'S', 'Wage Type', true);
$combo->add('Hourly', 'H');
$combo->add('Salary', 'S');
$form->addElement($combo);

$combo = new MultiComboBox('position', $position, 'Position', false);
$combo->add('Planner', 'P');
$combo->add('Manager', 'M');
$combo->add('Engineer', 'E');
$combo->add('Analyst', 'A');
$form->addElement($combo);

$form->addButton(new SubmitButton('submit', 'Submit'));
$form->addButton(new ResetButton('reset', 'Reset'));

if ($submit == 'Submit') {
$isValid = $form->validate();

if ($isValid) {
echo("everything okay");
// start processing info into database or whatever
} else {
echo($form->getErrorMessage());
$form->display();
$formEngine->displayJavascriptLibraryCode();
echo($form->generateJavaScriptCode());
}
} else {
$formEngine->displayJavascriptLibraryCode();
$form->display();
echo($form->generateJavaScriptCode());
}
```

What, no code about the implementation? What ever am I to do? That's an easy question to answer; write it. If you're going to learn OO and appreciate all the concepts that you've learned, your first attempt should be to complete this module. It's not an entire waste of time since you'll be able to use it *a lot* in your programs. Say goodbye to those free modules on the net and use something that you've created on your own, something that you can say you understand the foundation of, beyond the code.

## Summary

In this chapter, you've learned that object-oriented programming is essential for PHP to survive as the web platform of tomorrow. We've talked about OOP's development and benefits after the explanation of the "software crisis" – where programs became large, complex, and unmanageable and there was a need for better software construction. We then talked about how it differs from functional programming and discussed the benefits that OO provides for us programmers and architects – increased reusability and maintainability.

After we sorted out all the groundwork, we dove into the basic building blocks of an object-oriented program – classes and objects. We learned that objects contain methods, members, and a constructor and that they become instantiated for use in our program when we use PHP's new operator. We learned that by providing useful services that clients can use and hiding the data in our objects, we can increase the reusability and maintainability of our code. This characteristic was called encapsulation because all the details of the implementation were hidden inside the class, un-exposable to any client using the class.

We then talked about adding more structure and meaning to our objects by using inheritance and polymorphism. We figured out that inheritance gives us the ability to specialize objects by adding more behavior and data to them, making our code more traceable, as well as reusable. By using polymorphism on our inherited objects, we could develop generic, elegant solutions that dealt with the details at run time with the help of the PHP interpreter. This also increased maintainability since we could add new classes to our inheritance model without modifying the logic in any of our polymorphic code.

Lastly, we finished this discussion by talking about cohesion and coupling. Cohesion is how closely the elements and functionality are related within the object, and coupling is the degree of relatedness between two or more objects. Highly cohesive modules produce smaller, more maintainable modules while loosely coupled objects provide us with greater reusability. We learned that it's good practice to create highly cohesive, yet loosely coupled modules to have highly reusable and maintainable programs.

Next, we looked at object modeling using UML. We realized that UML offers an easy, consistent way for specifying our designs for ourselves as well as communicating ideas to other programmers. Then we talked about the different kinds of containment and saw that there was a difference between physical containment and containment for reuse, called delegation.

We further looked into some more design heuristics and good practices by seeing that logic must be in the proper place. We learned that if it's scattered around our program, that it will be harder to use our objects, thus making it harder to reuse them and maintain them.

Lastly, we looked at creating object models for relational databases and an object model for a very advanced form engine. We illustrated various cases of inheritance, polymorphism, good design heuristics, delegation, and UML.

## 6 Debugging

An often-overlooked aspect of programming projects is the amount of time needed for debugging and optimizing the programs. A PHP programming project is no different. In fact the unique environment in which PHP scripts are developed and deployed present specific challenges as well as new avenues to debug and optimize programs. However, the core concepts of planning for debugging and optimization remain the same as with traditional programming tools.

In this chapter we will take an in-depth look at the various programming pitfalls, their avoidance, and the tools at our disposal to minimize and thwart erroneous code. In this chapter we'll look at:

- An overview of the programming errors
- Error levels in PHP:
  - Parse errors
  - Fatal errors
  - Warnings and notices
  - Core and compile errors
  - User error levels
  - Setting the error reporting levels
- Defensive programming to minimize errors:
  - Suppressing error messages
  - Error recovery
  - Custom error checking
  - Logging errors
- Debugging and testing tools:
  - HTTP debugging utilities like telnet clients and snoop servers
  - Debugging by tracing using phpCodesite
  - Remote debuggers such as BODY and Zend IDE
  - Script testing using phpUnit

## Overview of Programming Errors

PHP, being a scripting language, offers us an opportunity to spot errors as the program is interpreted, while it also poses a problem since the scripts are often executed on a server and therefore not as accessible for debugging as traditional stand-alone programs. However, the class of errors that can be spotted while the script is interpreted is often just a small subset of the programming errors that creep into scripts. Some common programming errors encountered while coding PHP scripts are:

- Syntax errors
- Semantic errors
- Logical errors
- Environmental errors

Let us take a closer look at these errors now.

## Syntax Errors

Syntax errors are the most common and easily detected category of errors. These errors occur due to incorrect use of language constructs. Occurrence of syntax errors has significantly changed between PHP3 and PHP4. This is because, with PHP3, each line was interpreted as it was encountered, whereas with PHP4, the statements are compiled before they are executed.

With PHP3 a single successful run of a program does not guarantee that all syntactic errors have been weeded out. Most often special code-paths, taken by the script, unearth syntax errors that have not yet been discovered. To illustrate this, let us look at the following PHP3 script:

```php
<?php
//Simple_Leap.php

if ($year % 4) {
    // simplified test for a non-leap year
    echo("February has 28 days");
} else {
    echo("February has 29 days");
}
?>
```
