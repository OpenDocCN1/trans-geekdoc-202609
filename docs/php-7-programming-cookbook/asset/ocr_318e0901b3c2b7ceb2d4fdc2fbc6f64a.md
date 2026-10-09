```
```
 echo $a->getIntVal() ;
 echo PHP_EOL;

// NOTE: boolean TRUE == 1
$a->setIntVal(TRUE);
 echo $a->getIntVal();
 echo PHP_EOL;

// returns array() even though no value was set
 var_dump($a->getArrVal());
 echo PHP_EOL;

// sets a "proper" value
$a->setArrVal(['A','B','C']);
 var_dump($a->getArrVal());
 echo PHP_EOL;

 try {
 $a->setArrVal('this is not an array');
 var_dump($a->getArrVal());
 echo PHP_EOL;
 } catch (TypeError $e) {
 echo $e->getMessage();
 }

 echo PHP_EOL;
```
```

As you can see from the following output, setting a *proper* integer value works as expected. A non-numeric value defaults to 0. Interestingly, if you supply a Boolean `TRUE` as an argument to `setIntVal()`, it is interpolated to 1.

If you call `getArrVal()` without setting a value, the default is an empty array. Setting an array value works as expected. However, if you supply a non-array value as an argument, the type hint of the array causes a `TypeError` to be thrown, which can be caught as shown here: