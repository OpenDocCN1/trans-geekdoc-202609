```
```php
class Person {
    private $name;
    private $age;

    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }

    public function getName() {
        return $this->name;
    }

    public function getAge() {
        return $this->age;
    }

    public function setAge($age) {
        $this->age = $age;
    }
}
```
```

```
```php
$person1 = new Person("John Doe", 30);
echo "Name : " . $person1->getName() . "<br>";
```
```