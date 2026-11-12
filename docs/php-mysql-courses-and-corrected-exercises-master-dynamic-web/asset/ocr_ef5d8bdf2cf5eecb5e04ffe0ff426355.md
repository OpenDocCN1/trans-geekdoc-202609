# Two-dimensional associative array

In the $country table example, both rows and columns are indexed, which can sometimes make the designation of elements ambiguous. To remedy this, instead of using indices for the columns, we can use keys for better readability and a more intuitive understanding of the table.

| | Country | Capital | Inhabitant |
|---|---|---|---|
| 0 | France | Paris | 67 |
| 1 | Canada | Ottawa | 38 |
| 2 | Morocco | Rabat | 40 |
| 3 | Spain | Madrid | 47 |

To declare and initialize this array in PHP, we can use the bracket notation [] or the array() function:

# Method 1:

```
$country_information = array(
array("country" => "France", "capital" => "Paris", "inhabitants" => 67),
array("country" => "Canada", "capital" => "Ottawa", "inhabitants" => 38),
```