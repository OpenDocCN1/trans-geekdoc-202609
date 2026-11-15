FilterIterator is implemented in the CSVFilterIterator class. It inherits from Filter Iterator and only requires an accept() method in which you carry out the filtering.

In the constructor, pass the iterator object of the inner iterator and call the constructor. You also save the filter value in a property:

```
class CSVFilterIterator extends FilterIterator {
private $value;

public function __construct(CSVIterator $CSVIterator, $value) {
parent::__construct($CSVIterator);
$this->value = $value;
}
}
```

This is followed by filtering. To access the currently iterated element in the inner iterator, use the getInnerIterator() method and then current() for the value of the current element (or key() for the position):

```
public function accept() {
$ele = $this->getInnerIterator()->current();
if (strpos($ele, $this->value) !== 0) {
return true;
} else {
return false;
}
}
}
```

The filtering in this case is very simple. All values with a comma are filtered out. However, the example shows the benefits very clearly. You have an iterator and can then filter it from the outside — that is, with another class.

The following listing shows the complete code with the highlighted SPL elements. Figure 11.50 shows the output.

```
<?php
class CSVIterator implements Iterator {
private $csv;
private $position;

public function __construct($csv) {
$this->csv = explode(',', $csv);
}

public function next(): void {
$this->position += 1;
}

public function rewind(): void {
```