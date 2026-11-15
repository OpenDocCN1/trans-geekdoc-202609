In principle, the CSV class only accepts the string with the comma-separated values in the constructor. The getIterator() method is provided by IteratorAggregate and instantiates the actual iterator object:

```
class CSV implements IteratorAggregate {
private $csv;
public function __construct($csv = '') {
$this->csv = $csv;
}

public function getIterator() {
return new CSVIterator($this->csv);
}
}
```

The Iterator object is instantiated by the CSVIterator class, which you must also write yourself. It implements the Iterator interface, which is predefined by PHP. The method defined in this interface needs the foreach loop to know how to iterate through the respective values. Let's go through this class method by method:

+   The class itself implements the Iterator class. One property is intended for the array with the CSV values, the other for the current position of the iterator:

```
class CSVIterator implements Iterator {
private $csv;
private $position;
}
```

+   In the constructor, the transferred CSV string is separated using commas and assigned to the property:

```
public function __construct($csv) {
$this->csv = explode(',', $csv);
}
```

+   The next() method controls the step-by-step iteration of the iterator. Here, the position is simply incremented by 1:

```
public function next() {
$this->position += 1;
}
```

+   To return to the first starting position, the rewind() method sets the position to 0:

```
public function rewind() {
$this->position = 0;
}
```

+   key() returns the current position, which corresponds to the index of the array:

```
public function key() {
return $this->position;
}
```