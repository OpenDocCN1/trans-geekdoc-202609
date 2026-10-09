```
const VALIDATOR_NOT_FOUND = 'Validator not found.\
    Run setValidator()';

protected $filter;
protected $validator;
protected $data;

public function setFilter(Filter $filter)
{
    $this->filter = $filter;
}

public function setValidator(Validator $validator)
{
    $this->validator = $validator;
}

public function setData($data)
{
    $this->data = $data;
}
```

+   3. Next, we define a `validate()` method that calls the `process()` method of the embedded `Application\Filter\Validator` instance. We check to see if `$data` and `$validator` exist. If not, the appropriate exceptions are thrown with instructions on which method needs to be run first:

```php
public function validate()
{
    if (!$this->data)
        throw new RuntimeException(self::DATA_NOT_FOUND);

    if (!$this->validator)
        throw new RuntimeException(self::VALIDATOR_NOT_FOUND);
```

+   4. After calling the `process()` method, we associate validation result messages with form element messages. Note that the `process()` method returns a boolean value that represents the overall validation status of the data set. When the form is re-displayed following failed validation, error messages will appear next to each element:

```php
$valid = $this->validator->process($this->data);

foreach ($this->elements as $element) {
    if (isset($this->validator->getResults()
        [$element->getName()])) {
        $element->setErrors($this->validator->getResults()