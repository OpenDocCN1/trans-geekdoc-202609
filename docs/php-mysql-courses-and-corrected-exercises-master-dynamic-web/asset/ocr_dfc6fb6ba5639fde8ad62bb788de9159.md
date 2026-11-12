```
private $number_doors;

public function __construct($brand, $model, $year, $price, $number_doors) {
    parent::__construct($brand, $model, $year, $price);
    $this->number_doors = $number_doors;
}

public function getNumberDoors() {
    return $this->number_doors;
}

public function setNumberDoors($number_doors) {
    $this->number_doors = $number_doors;
}

public function display() {
    parent::display();
    echo " - ".$this->number_doors." doors";
}
}

// Create an object of type Car
$car1 = new Car("Mercedes", "C220", 2024, 45000, 5);
$car1->display();
```