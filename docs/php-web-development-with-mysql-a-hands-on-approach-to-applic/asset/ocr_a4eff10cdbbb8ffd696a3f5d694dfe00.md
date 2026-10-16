# Multidimensional Arrays

X- and Y-axis, which might represent points contained in an area. Taking this example one step further, a three-dimensional array could represent the X-, Y-, and Z-axis, representing points contained in a volume.

Multidimensional arrays work for both numeric and associative arrays. Listing 6.8 is an example of creating and accessing a two-dimensional numeric array holding a simple grid for a “Battleship” game.

```
```php
$battleship_grid = [
    ["miss", "miss", "miss"],
    ["miss", "miss", "hit"],
    ["miss", "miss", "hit"],
    ["miss", "miss", "hit"]
];

// Coordinates to sink my battleship
echo "{$battleship_grid[1][3]}",
"{$battleship_grid[2][3]}",
"{$battleship_grid[3][3]}";
```
```

Results in:

hit, hit, hit

Listing 6.9 is an example of how to create and access a two-dimensional associative array holding some of the cities keyed by the state that Oscar and I have lived in.

```
```php
$sus_cities_we_lived_in = [
    "Ken" => [
        "California" => "San Diego",
        "Florida" => "Orlando",
        "Wisconsin" => "Madison"
    ],
    "Oscar" => [
        "New York" => "New York",
        "Maryland" => "Baltimore",
        "Virginia" => "Richmond"
    ]
];

echo "I live in {$sus_cities_we_lived_in['Ken']['Wisconsin']}<br/>";
echo "and Oscar lives in {$sus_cities_we_lived_in['Oscar']['Virginia']}";
```
```