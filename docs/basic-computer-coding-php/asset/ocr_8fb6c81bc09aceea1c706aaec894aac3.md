# Basic Computer Coding: PHP

```
$addresses[0] = "spam@cyberpromo.net";necho $addresses;    // prints "Array"
```

Using simple assignment to initialize an array in your program can lead to code like this:

```
$addresses[0] = "spam@cyberpromo.net"
$addresses[1] = "abuse@example.com"
$addresses[2] = "root@example.com"
```

That's an indexed array, with integer indices beginning at 0. Here's an associative array:

```
$price['gasket'] = 15.29
$price['wheel'] = 75.25
$price['tire'] = 50.00;
```

An easier way to initialize an array is to use the array() construct, which builds an indexed array, and the index values (starting at 0) are created automatically:

```
$addresses = array("spam@cyberpromo.net", "abuse@example.com", "root@example.com");
```

To create an associative array with array(), use the => symbol to separate indices (keys) from values:

```
$price = array(
'gasket' => 15.29,
'wheel' => 75.25,
'tire' => 50.00
);
```

> The use of whitespace and alignment. We could have bunched the code, but it would not have been as easy to read (this is equivalent to the previous code), or as composed of (key, value) pairs, such that each possible is easy to add or remove values:

Associative array is an data type composed of a collection of (key, value) pairs, each at once in the collection.

```
$price = array('gasket' => 15.29, 'wheel' => 75.25,
'tire' => 50.00);
```

You can also specify an array using a shorter, alternate syntax:

```
$days = ['gasket' => 15.29, 'wheel' => 75.25,
'tire' => 50.0];
```