are grouped together in a main table to form the complete multi-dimensional array. There are several methods for declaring and initializing this array in PHP.

# Method 1: Use the array() function to create an array.

```
<?php
$info_country = array(
    array("France", "Paris", 67),
    array("Canada", "Ottawa", 38),
    array("Morocco", "Rabat", 40),
    array("Spain", "Madrid", 47)
);
?>
```

# Method 2: Using bracket notation [ ].

```
<?php
$info_country = [
    ["France" , "Paris", 67],
    ["Canada", "Ottawa", 38],
    ["Morocco", "Rabat", 40],
    ["Spain", "Madrid", 47]
]
```