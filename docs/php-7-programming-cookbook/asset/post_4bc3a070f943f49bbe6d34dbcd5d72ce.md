
The actual display logic is identical to the radio button recipe, except that we need to render two separate HTML select instances:

```
<form name="status" method="get">  
<table id="status" class="display" cellpadding="0" width="100%">  
<tr><?= $status1->render(); ?>\</tr>  
<tr><?= $status2->render(); ?>\</tr>  
<tr><?= $submit->render(); ?>\</tr>  
<tr>  
<td colspan=2>  
<br>  
<pre>  
<?php var_dump($_GET); ?>  
</pre>  
</td>  
</tr>  
</table>  
</form>
```

Here is the actual output:

![](img/39390f6d56c5a83b28db083a8bd5185c_211_0.png)

Also, you can see how the elements appear in the view source page:

![](img/39390f6d56c5a83b28db083a8bd5185c_212_0.png)

## Implementing a form factory

The purpose of a form factory is to generate a usable form object from a single configuration array. The form object should have the ability to retrieve the individual elements it contains so that output can be generated.

### How to do it...

- 1. First, let's create a class called `Application\Form\Factory` to contain the factory code. It will have only one property, `$elements`, with a getter:

```
namespace Application\Form;

class Factory
{
    protected $elements;
    public function getElements()
    {
        return $this->elements;
    }
    // remaining code
}
```

- 2. Before we define the primary form generation method, it's important to consider what configuration format we plan to receive, and what exactly the form generation will produce. For this illustration, we will assume that the generation will produce a `Factory` instance, with an `$elements` property. This property would be an array of `Application\Form\Generic` or `Application\Form\Element` classes.

- 3. We are now ready to tackle the `generate()` method. This will cycle through the configuration array, creating the appropriate `Application\Form\Generic` or `Application\Form\Element\*` objects, which in turn will be stored in the `$elements` array. The new method will accept the configuration array as an argument. It is convenient to define this method as static so that we can generate as many instances as are needed using different blocks of configuration.

- 4. We create an instance of `Application\Form\Factory`, and then we start looping through the configuration array:

```
public static function generate(array $config)
{
    $form = new self();
    foreach ($config as $key => $p) {
```

- 5. Next, we check for parameters that are optional in the constructor for the `Application\Form\Generic` class:

```
$p['errors'] = $p['errors'] ?? array();
$p['wrappers'] = $p['wrappers'] ?? array();
$p['attributes'] = $p['attributes'] ?? array();
```

- 6. Now that all the constructor parameters are in place, we can create the form element instance, which is then stored in `$elements`:

```
$form->elements[$key] = new $p['class']
(
    $key,
    $p['type'],
    $p['label'],
    $p['wrappers'],
    $p['attributes'],
    $p['errors']
);
```

- 7. Next, we turn our attention to options. If the options parameter is set, we extract the array values into variables using `list()`. We then test the element type using `switch()` and run `setOptions()` with the appropriate number of parameters:

```
if (isset($p['options'])) {
    list($a,$b,$c,$d) = $p['options'];
    switch ($p['type']) {
        case Generic::TYPE_RADIO    :
```

```
$form->elements[$key]->setOptions($a,$b,$c,$d);
break;
case Generic::TYPE_SELECT    :
$form->elements[$key]->setOptions($a,$b);
break;
default    :
$form->elements[$key]->setOptions($a,$b);
break;
}
}
```

- 8. Finally, we return the form object and close out the method:

```
return $form;
}
```

- 9. Theoretically, at this point, we could easily render the form in our view logic by simply iterating through the array of elements and running the `render()` method. The view logic might look like this:

```
<form name="status" method="get">
<table id="status" class="display" cellspacing="0" width="100%">
<?php foreach ($form->getElements() as $element) : ?>
<?php echo $element->render(); ?>
<?php endforeach; ?>
</table>
</form>
```

- 10. Finally, we return the form object and close out the method.

- 11. Next, we need to define a discrete `Form` class under `Application\Form\Element`:

```
namespace Application\Form\Element;
class Form extends Generic
{
    public function getInputOnly()
    {
        $this->pattern = '<form name="$s" $s> ' . PHP_EOL;
        return sprintf($this->pattern, $this->name,
                       $this->getAttribs());
    }
    public function closeTag()
    {
        return '</' . $this->type . '>';
    }
}
```

- 12. Returning to the `Application\Form\Factory` class, we now need to define a simple method that returns a `sprintf()` wrapper pattern that will serve as an envelope for input. As an example, if the wrapper is `div` with an attribute `class="test"` we would produce this pattern: `<div class="test">%s</div>`. Our content would then be substituted in place of `%s` by the `sprintf()` function:

```
protected function getWrapperPattern($wrapper)
{
    $type = $wrapper['type'];
    unset($wrapper['type']);
    $pattern = '<' . $type;
    foreach ($wrapper as $key => $value) {
        $pattern .= ' ' . $key . '="' . $value . '"';
    }
    $pattern .= '>%s</' . $type . '>';
    return $pattern;
}
```

- 13. Finally, we are ready to define a method that does overall form rendering. We obtain wrapper `sprintf()` patterns for each form row. We then loop through the elements, render each one, and wrap the output in the row pattern. Next, we generate an `Application\Form\Element\Form` instance. We then retrieve the form wrapper `sprintf()` pattern and check the `form_tag_inside_wrapper` flag, which tells us whether we need to place the form tag inside or outside the form wrapper.

```
public static function render($form, $formConfig)
{
    $rowPattern = $form->getWrapperPattern(
        $formConfig['row_wrapper']);
    $contents = '';
    foreach ($form->getElements() as $element) {
        $contents .= sprintf($rowPattern, $element->render());
    }

    $formTag = new Form($formConfig['name'],
                        Generic::TYPE_FORM,
                        '',
                        array(),
                        $formConfig['attributes']);

    $formPattern = $form->getWrapperPattern(
        $formConfig['form_wrapper']);
    if (isset($formConfig['form_tag_inside_wrapper'])
        && !$formConfig['form_tag_inside_wrapper']) {
        $formPattern = '%s' . $formPattern . '%s';
        return sprintf($formPattern, $formTag->getInputOnly(),
                       $contents, $formTag->closeTag());
    } else {
        return sprintf($formPattern, $formTag->getInputOnly())
            . $contents . $formTag->closeTag();
    }
}
```

### How it works...

Referring to the preceding code, create the `Application\Form\Factory` and `Application\Form\Element\Form` classes.

Next, you can define a `chap_06_form_factory.php` calling script that sets up autoloading and anchors the new class:

```
<?php
require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../../');
use Application\Form\Generic;
use Application\Form\Factory;
```

Next, define the wrappers using the `$wrappers` array defined in the first recipe. You can also use the `$statusList` array defined in the second recipe.

See if there is any status input from `$_POST`. Any input will become the selected key. Otherwise, the selected key is the default.

```
$email    = $_POST['email']      ?? '';
$checked0 = $_POST['status0']     ?? 'U';
$checked1 = $_POST['status1']     ?? 'U';
$checked2 = $_POST['status2']     ?? ['U'];
$checked3 = $_POST['status3']     ?? ['U'];
```

Now you can define the overall form configuration. The name and attributes parameters are used to configure the `form` tag itself. The other two parameters represent form-level and row-level wrappers. Lastly, we provide a `form_tag_inside_wrapper` flag to indicate that the form tag should not appear inside the wrapper (that is, `<table>`). If the wrapper was `<div>`, we would set this flag to TRUE:

```
$formConfig = [
    'name'       => 'status_form',
    'attributes' => ['id'=>'statusForm', 'method'=>'post',
                     'action'=>'chap_06_form_factory.php'],
    'row_wrapper' => [ 'type' => 'tr', 'class' => 'row'],
    'form_wrapper' => ['type'=>'table', 'class'=>'table',
                       'id'=>'statusTable',
```
