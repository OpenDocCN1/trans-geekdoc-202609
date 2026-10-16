```
```php
}
class MyDerivedClass extends MyBaseClass {
    protected $value2 = null;

    public function __construct($value1 = null,
        $value2 = null) {
        if ($value1 !== null) {
            parent::__construct($value1);
            if ($value2 !== null) {
                $this->value2 = $value2;
            }
        }
    }

    public function getValue2() {
        return $this->value2;
    }
}

$c = new MyDerivedClass('abc', 'def');
echo '1: ', $c->getValue1(), ', 2: ', $c->getValue2();
?>
```
```

*Using Inheritance with PHP (extends.php)*

**NOTE:** PHP does not support multiple inheritance. so one class may be derived only from (exactly) one other class. Of course, you could derive class B from class A, and class C from class B, so that class C also inherits public and protected methods from A.