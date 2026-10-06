# Chapter 6: Arrays

This is where sort() and asort() come in. They work just like sort() and rsort(), but they preserve the association between each element's key and its value:

```
$myBook = array("title" => "Bleak House",
"author" => "Dickens",
"year" => 1853);

// Displays Array ([title] => Bleak House [author] => Dickens [year] => 1853])
asort($($myBook);
print_r($myBook);

// Displays Array ([year] => 1853 [author] => Dickens [title] => Bleak House)
asort($$myBook);
print_r($myBook);
```

Note that although you can use asort() and sort() on indexed arrays, they're commonly used with associative arrays.

# Sorting Associative Array Keys with ksort() and rsort()

ksort() and rsort() behave in the same way as asort() and rsort(), respectively, preserving the associations between keys and values in ascending and descending order. The only difference is that, whereas asort() and rsort() sort elements by value, ksort() and rsort() sort the elements by their keys:

```
$myBook = array("title" => "Bleak House",
"author" => "Dickens",
"year" => 1853);
```

```
// Displays Array ([author] => Dickens [title] => Bleak House [year] => 1853])
ksort($$myBook);
print_r($myBook);
```

```
// Displays Array ([year] => 1853 [title] => Bleak House [author] => Dickens)
rsort($$myBook);
print_r($myBook);
```

In this example, ksort() has sorted the array by key in ascending order("title", "year"), whereas rsort() has sorted by key in the opposite order.

> As asort() and rsort(), ksort() and rsort() tend to be used mainly with associative arrays.