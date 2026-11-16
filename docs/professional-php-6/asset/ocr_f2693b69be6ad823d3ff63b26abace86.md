```
$key = sizeof($this->_members) - 1;
};
$this->_keys[] = $key;
$this->position = sizeof($this->_members);
}
public function key( ) {
    return($this->_keys[$this->position]);
}
public function next( ) {
    ++$this->position;
}
public function valid( ) {
    return(isset($this->_members[$this->position]));
}
public function length( ) {
    return sizeof($this->_members);
}
public function exists($key) {
    // resolve key to index
    $idx = -1;
    for ($i=0; $i<=sizeof($this->_keys)-1; $i++) {
    if ($this->_keys[$i] = $key) {
        $idx = $i;
    };
    }
    if ($idx == -1) {
        return(false);
    };
    return (isset($this->_members[$i]));
}
}
?>
```

With the collections class in place, you can code up a communication class to make use of it.

# The Communications Class Itself

Take a look at the following code, which you should save as communication.php. Note that it makes use of the simple collection class you just wrote in order to store its collection of recipients:

```
<?php
abstract class Communication {
protected $arRecipientCollection;
private $strMessage;
```