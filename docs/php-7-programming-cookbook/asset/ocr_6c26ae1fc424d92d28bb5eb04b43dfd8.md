+   8. Inside the foreach() loop we check to see if the key is the one selected. If so, the $checked attribute is added for that radio button. We then call the parent class getInputOnly() method to return the HTML for each button. Note that the value attribute of the input element is the options array key. The button label is the options array element value:

```
```
foreach ($this->options as $key => $value) {
    $this->attributes['id'] = $baseId . $count++;
    $this->attributes['value'] = $key;
    if ($key == $this->selectedKey) {
        $this->attributes['checked'] = '';
    } elseif (isset($this->attributes['checked'])) {
        unset($this->attributes['checked']);
    }

    if ($this->after) {
        $html = parent::getInputOnly() . $value;
    } else {
        $html = $value . parent::getInputOnly();
    }
    $output .= $this->spacer . $html;
}
return $output;
```
```

# How it works...

Copy the preceding code into a new Radio.php file in the Application/Form/Element folder. You can then define a chap_06_form_element_radio.php calling script that sets up autoloading and anchors the new class:

```
```
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
use Application\Form\Generic;
use Application\Form\Element\Radio;
```
```

Next, define the wrappers using the $wrappers array defined in the previous recipe.

Then you can define a $status array and create an element instance by passing parameters to the constructor:

```
```
$statusList = [
    'U' => 'Unconfirmed',
    'P' => 'Pending',
    'T' => 'Temporary Approval',
    'A' => 'Approved'
```
```