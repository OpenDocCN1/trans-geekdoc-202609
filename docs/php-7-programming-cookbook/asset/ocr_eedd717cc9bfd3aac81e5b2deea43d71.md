+   8. As you will recall, each *assignment* is *keyed* to the data field, and represents an array of callbacks for that field. Thus, in `processGlobalAssignment()`, we need to loop through the array of callbacks. In this case, however, because these *assignments* are **global**, we also need to loop through the **entire** data set, and apply each global filter in turn.

+   9. In contrast to the equivalent `Application\Filter\Filter::processGlobalAssignment()` method, we need to call `mergeValidationResults()`. The reason for this is that if the value of `$result->item` is already `FALSE`, we need to ensure that it does not subsequently get overwritten by a value of `TRUE`. Any validator in the chain that returns `FALSE` must overwise any other validation result:

```php
protected function processGlobalAssignment($assignment, $data)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        foreach ($data as $k => $value) {
            $result = $this->callbacks[$callback['key']]
                     ($value, $callback['params']);
            $this->results[$k]->mergeValidationResults($result);
        }
    }
}
```


+   10. When we define `processAssignment()`, in a manner akin to `processGlobalAssignment()`, we need to execute **each remaining callback assigned** to each data key, again calling `mergeValidationResults()`: 

```php
protected function processAssignment($assignment, $key, $value)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        $result = $this->callbacks[$callback['key']]
                  ($value, $callback['params']);
        $this->results[$key]->mergeValidationResults($result);
    }
}
```

# How it works...

As with the preceding recipe, be sure to define the following classes:

+   ▶ `Application\Filter\Result`

▶ `Application\Filter\CallbackInterface`