+   7. We replace the default value for `$pattern` with `<select name="$s" %s>`. We then loop through the attributes, adding them as key-value pairs with spaces in between:

```
```php
protected function getSelect()
{
    $this->pattern = '<select name="$s" %s> ' . PHP_EOL;
    return sprintf($this->pattern, $this->name,
                    $this->getAttrs());
}
```
```

+   8. Next, we define a method to obtain the `option` tags that will be associated with the `select` tag.

+   9. As you will recall, the *key* from the `$this->options` array represents the return value, whereas the *value* part of the array represents the text that will appear on screen. If `$this->selectedKey` is in array form, we check to see if the *value* is in the array. Otherwise, we assume `$this->selectedKey` is a string and we simply determine if it is equal to the key. If the selected key matches, we add the *selected* attribute:

```
```php
protected function getOptions()
{
    $output = '';
    foreach ($this->options as $key => $value) {
        if (is_array($this->selectedKey)) {
            $selected = (in_array($key, $this->selectedKey))
                        ? ' selected' : '';
        } else {
            $selected = ($key == $this->selectedKey)
                        ? ' selected' : '';
        }
        $output .= '<option value="" . $key . '"
                   . $selected
                   . '></>'
                   . $value
                   . '</option>';
    }
    return $output;
}
```
```

+   10. Finally we are ready to override the core `getInputOnly()` method.

+   11. You will note that the logic for this method only needs to capture the return values from the `getSelect()` and `getOptions()` methods described in the preceding code. We also need to add the closing `</select>` tag:

```
```php
public function getInputOnly()
{
    $output = $this->getSelect();
    $output .= $this->getOptions();
```

```