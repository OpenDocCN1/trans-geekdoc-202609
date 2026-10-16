# Useful Array Functions

Results in:

```
```
Array
(
[0] => California
[1] => Wisconsin
)
```
```

Listing 6.6 is an example that replaces the removed section with all the elements in another array.

```
```
$Sus_states = [
    "California",
    "Arizona",
    "Florida",
    "Wisconsin"
];
$more_us_states = ["Virginia", "New York"];
// Removes 'Arizona' and 'Florida', and replaces
// them with 'Virginia' and 'New York'
array_splice($Sus_states, 1, 2, $more_us_states);
echo "<pre>";
print_r($Sus_states);
echo "</pre>";
```
```

Results in:

```
```
Array
(
[0] => California
[1] => Virginia
[2] => New York
[3] => Wisconsin
)
```
```