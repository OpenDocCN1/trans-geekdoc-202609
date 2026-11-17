# Altering a Form Object

When you use a form class definition, the form is defined outside the action. That makes dynamic default value assignment quite difficult. That's why the form object takes an array of default values as its first argument:

```
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new ContactForm(array('email' => 'me@example.com'));
```

You can also override existing widget or validator settings by calling setWidget() or setValidator() on an existing field name.

However, widgets and validators are objects in symfony, and offer a clean API to modify their properties:

```
// in modules/foo/actions/actions.class.php
// Define the form
$this->form = new ContactForm();

// Allow multiple language selections
$form->getWidget('language')->setOption('multiple', true);

// Add a 'gender' list of options widget
$form->setWidget('gender', new sfWidgetFormChoice(array('expanded' =>
true, 'choices' => array('m' => 'Male', 'f' => 'Female')), array('class'
=> 'gender_list')));

// Change the HTML attributes of the 'subject' widget
$form->getWidget('subject')->setAttribute('disabled', 'disabled');

// Remove the 'subject' field
unset($form['subject'])

// Note: You cannot remove just the widget. Removing a widget will also
remove the related validators

// Change the 'min_length' error in the 'message' validator
$form->getValidator('message')->setMessage('min_length', 'Message too
short');

// Make the 'name' field optional
$form->getValidator('name')->setOption('required', false);
```

# Custom Widget and Validator classes

A custom widget is simply a class extending sfWidgetForm, and providing a configure() and a render() methods. Check the code of existing widget classes for a deeper understanding of the widgets system. The next listing exposes the code of the sfWidgetFormInput widget to illustrate the widget structure:

```
class sfWidgetFormInputText extends sfWidgetForm
{
/**
 * Configures the current widget.
 *
 * This method allows each widget to add options or HTML attributes
 * during widget creation.
 *
 * Available options:
 *  * type: The widget type (text by default)
 *
 * @param array $options     An array of options
 * @param array $attributes  An array of default HTML attributes
```