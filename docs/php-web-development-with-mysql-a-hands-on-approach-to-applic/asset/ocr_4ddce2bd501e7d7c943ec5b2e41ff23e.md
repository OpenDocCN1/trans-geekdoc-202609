# Listing 6.2.

```
```php
1. $us_state_capitals = [
2.     "California" => "Sacramento",
3.     "Florida" => "Tallahassee",
4.     "Wisconsin" => "Madison"
5. ];
6. 
7. echo "<pre>";
8. print_r(array_keys($us_state_capitals));
9. echo "</pre>";
```
```

Results in:

```
```
Array
(
    [0] => California
    [1] => Florida
    [2] => Wisconsin
)
```
```

Here is an example if you are only looking for a key (or keys) mapped to a value (or values) contained in an array as in Listing 6.3.

# Listing 6.3.

```
```php
1. $us_state_capitals = [
2.     "California" => "Sacramento",
3.     "Florida" => "Tallahassee",
4.     "Wisconsin" => "Madison"
5. ];
6. 
7. echo "<pre>";
8. print_r(array_keys($us_state_capitals, "Madison"));
9. echo "</pre>";
```
```

Results in:

```
```
Array
(
    [0] => Wisconsin
)
```
```