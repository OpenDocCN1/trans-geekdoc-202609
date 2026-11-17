# Standard Widgets

Here is a list of available widget types, and how they translate into HTML (via renderRow()):

```
// Text input
$form->setWidget('full_name', new sfWidgetFormInput(array('default' => 'John Doe')));
<label for="full_name">Full Name</label>
<input type="text" name="full_name" id="full_name" value="John Doe" />
// Textarea
$form->setWidget('address', new sfWidgetFormTextarea(array('default' => 'Enter your address here'), array('cols' => 20, 'rows' => 5)));
<label for="address">Address</label>
<textarea name="address" id="address" cols="20" rows="5">Enter your address here</textarea>
// Password input
// Note that 'password' type widgets don't take a 'default' parameter for security reasons
$form->setWidget('pwd', new sfWidgetFormInputPassword());
<label for="pwd">Pwd</label>
<input type="password" name="pwd" id="pwd" />
// Hidden input
$form->setWidget('id', new sfWidgetFormInputHidden(array('default' => 1234)));
<input type="hidden" name="id" id="id" value="1234" />
// Checkbox
$form->setWidget('single', new sfWidgetFormInputCheckbox(array('value_attribute_value' => 'single', 'default' => true)));
<label for="single">Single</label>
<input type="checkbox" name="single" id="single" value="true" checked="checked" />
```

There are more options available for each widget than what is exposed here. Check the widget API documentation for a complete description of what each widget expects and how it renders.

# List Widgets

Whenever users have to make a choice in a list of values, and whether they can select one or many option in this list, a single widget answers all the needs: the choice widget. According to two optional parameters (multiple and expanded), this widget renders in a different way:

| | multiple=false (default) | multiple=true |
| --- | --- | --- |
| expanded=false (default) | Dropdown list (`<select>`) | Dropdown box (`<select multiple>`) |
| expanded=true | List of Radiobuttons | List of checkboxes |