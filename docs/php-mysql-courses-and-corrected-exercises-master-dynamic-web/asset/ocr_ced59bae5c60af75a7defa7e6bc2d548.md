```
```php
$this->model = $model;
}

public function getYear() {
	return $this->year;
}

public function setYear($year) {
	$this->year = $year;
}

public function getPrice() {
	return $this->price;
}

public function setPrice($price) {
	$this->price = $price;
}

public function display() {
	echo "Vehicle ".$this->brand.". ".$this->model." year ".$this->year." - Price: ".$this->price." euros";
}
}
```
```