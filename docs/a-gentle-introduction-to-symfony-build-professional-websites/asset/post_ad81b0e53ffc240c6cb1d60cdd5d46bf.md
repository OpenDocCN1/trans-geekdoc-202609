
You can be more accurate and define an additional parameter to force the position where to include the file (first or last position), as shown in Listing 7-33. This works for both style sheets and JavaScript files.

## Listing 7-33 - Defining the Position of the Included Asset

```
// In the view.yml
indexSuccess:
  stylesheets: [special: { position: first }]

// In the action
$this->getResponse()->addStylesheet('special', 'first');

// In the template
```

You can also decide to bypass the transformation of the asset file name, so that the resulting <link> or <script> tags refer to the exact location specified, as shown in Listing 7-34.

## Listing 7-34 - Style Sheet Inclusion with Raw Name

```
// In the view.yml
indexSuccess:
  stylesheets: [main, paper: { raw_name: true }]

// In the Action
$this->getResponse()->addStylesheet('main', '', array('raw_name' => true));

// In the template
true)) ?>

// Resulting View
<link rel="stylesheet" type="text/css" href="main" />
```

To specify media for a style sheet inclusion, you can change the default style sheet tag options, as shown in Listing 7-35.

## Listing 7-35 - Style Sheet Inclusion with Media

```
// In the view.yml
indexSuccess:
  stylesheets: [main, paper: { media: print }]

// In the Action
$this->getResponse()->addStylesheet('paper', '', array('media' =>
  'print'));

// In the template
'print')) ?>

// Resulting View
<link rel="stylesheet" type="text/css" media="print" href="/css/paper.css" />
```

> **Note about assets inclusions using the view.yml file**
> 
> The best practice is to define the defaults stylesheets and javascripts file in the project view.yml file, and include specifics stylesheets or javascripts files in your templates using the dedicated helper. This way, you do not have to remove or replace already included assets, which can be a painful in some cases.

## Layout Configuration

According to the graphical charter of your website, you may have several layouts. Classic websites have at least two: the default layout and the pop-up layout.

You have already seen that the default layout is myproject/apps/frontend/templates/layout.php. Additional layouts must be added in the same global templates/ directory. If you want a view to use a frontend/templates/my_layout.php file, use the syntax shown in Listing 7-36.

```
Listing 7-36 - Layout Definition

// In view.yml
indexSuccess:
  layout: my_layout

// In the action
$this->setLayout('my_layout');

// In the template
<?php decorate_with('my_layout') ?>
```

Some views don't need any layout at all (for instance, plain text pages or RSS feeds). In that case, set has_layout to false, as shown in Listing 7-37.

```
Listing 7-37 - Layout Removal

// In `view.yml`
indexSuccess:
  has_layout: false

// In the Action
$this->setLayout(false);

// In the template
<?php decorate_with(false) ?>
```

> Ajax actions views have no layout by default.

## Output Escaping

When you insert dynamic data in a template, you must be sure about the data integrity. For instance, if data comes from forms filled in by anonymous users, there is a risk that it may include malicious scripts intended to launch cross-site scripting (XSS) attacks. You must be able to escape the output data, so that any HTML tag it contains becomes harmless.

As an example, suppose that a user fills an input field with the following value:

```
<script>alert(document.cookie)</script>
```

If you echo this value without caution, the JavaScript will execute on every browser and allow for much more dangerous attacks than just displaying an alert. This is why you must escape the value before displaying it, so that it becomes something like this:

```
&lt;script&gt;alert(document.cookie)&lt;/script&gt;
```

You could escape your output manually by enclosing every unsure value in a call to htmlspecialchars(), but that approach would be very repetitive and error-prone. Instead, symfony provides a special system, called output escaping, which automatically escapes every variable output in a template. It is activated by default in the application settings.yml.

## Activating Output Escaping

Output escaping is configured globally for an application in the settings.yml file. Two parameters control the way that output escaping works: the strategy determines how the variables are made available to the view, and the method is the default escaping function applied to the data.

Basically, all you need to do to activate output escaping is to set the escaping_strategy parameter to true (which is the default), as shown in Listing 7-38.

Listing 7-38 - Activating Output Escaping, in frontend/config/settings.yml

```
all:
  .settings:
    escaping_strategy: true
    escaping_method:  ESC_SPECIALCHARS
```

This will add htmlspecialchars() to all variable output by default. For instance, suppose that you define a test variable in an action as follows:

```
$this->test = '<script>alert(document.cookie)</script>';
```

With output escaping turned on, echoing this variable in the template will output the escaped data:

```
echo $test;
=> &lt;script&gt;alert(document.cookie)&lt;/script&gt;
```

In addition, every template has access to an $sf_data variable, which is a container object referencing all the escaped variables. So you can also output the test variable with the following:

```
echo $sf_data->get('test');
=> &lt;script&gt;alert(document.cookie)&lt;/script&gt;
```

> The $sf_data object implements the Array interface, so instead of using the $sf_data->get('myvariable'), you can retrieve escaped values by calling $sf_data['myvariable']. But it is not a real array, so functions like print_r() will not work as expected.

$sf_data also gives you access to the unescaped, or raw, data. This is useful when a variable stores HTML code meant to be interpreted by the browser, provided that you trust this variable. Call the getRaw() method when you need to output the raw data.

```
echo $sf_data->getRaw('test');
=> <script>alert(document.cookie)</script>
```

You will have to access raw data each time you need variables containing HTML to be really interpreted as HTML.

When escaping_strategy is false, $sf_data is still available, but it always returns raw data.

## Escaping Helpers

Escaping helpers are functions returning an escaped version of their input. They can be provided as a default escaping_method in the settings.yml file or to specify an escaping method for a specific value in the view. The following escaping helpers are available:

- ESC_RAW: Doesn't escape the value.
- ESC_SPECIALCHARS: Applies the PHP function htmlspecialchars() to the input.
- ESC_ENTITIES: Applies the PHP function htmlentities() to the input with ENT_QUOTES as the quote style.
- ESC_JS: Escapes a value to be put into a JavaScript string that is going to be used as HTML. This is useful for escaping things where HTML is going to be dynamically changed using JavaScript.
- ESC_JS_NO_ENTITIES: Escapes a value to be put into a JavaScript string but does not add entities. This is useful if the value is going to be displayed using a dialog box (for example, for a myString variable used in javascript:alert(myString);).

## Escaping Arrays and Objects

Output escaping not only works for strings, but also for arrays and objects. Any values that are objects or arrays will pass on their escaped state to their children. Assuming your strategy is set to true, Listing 7-39 demonstrates the escaping cascade.

Listing 7-39 - Escaping Also Works for Arrays and Objects

```
// Class definition
class myClass
{
  public function testSpecialChars($value = '')
  {
    return '<'.$value.'>';
  }
}

// In the action
$this->test_array = array('&', '<', '>');
$this->test_array_of_arrays = array(array('&'));
$this->test_object = new myClass();

// In the template
<?php foreach($test_array as $value): ?>
<?php echo $value ?>
<?php endforeach; ?>
=> &amp; &lt; &gt;
<?php echo $test_array_of_arrays[0][0] ?>
=> &amp;
<?php echo $test_object->testSpecialChars('&') ?>
=> &lt;&amp;&gt;
