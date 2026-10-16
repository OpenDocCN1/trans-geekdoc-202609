```
```php
public function offsetGet($offset) {
    //return (isset($this->_data[$offset])) ?
    $this->_data[$offset] : null;
    return ($this->offsetExists($offset)) ?
    $this->_data[$offset] : null;
}

/* Countable Interface */
public function count() {
    return count($this->_data);
}
}

$a = new MyArray();
$a[0] = 'I';
$a[1] = 'II';
$a[2] = 'III';
$a[3] = 'IV';
for ($i = 0; $i < count($a); $i++) {
    printf('<p>%s</p>', htmlspecialchars($a[$i]));
}
?>
```
```

*Using an Object Like an Array with SPL (splArray.php)*

SPL, the Standard PHP Library, is one of the most underrated features of PHP. It basically offers a huge set of interfaces. If you create a class using one of those interfaces, you might use standard PHP functions with your class. The documentation at http://php.net/spl is not always as detailed as you would expect, but it does give you some great pointers as to what is possible.