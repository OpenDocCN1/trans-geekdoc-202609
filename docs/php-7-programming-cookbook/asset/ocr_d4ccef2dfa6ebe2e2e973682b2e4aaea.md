And finally, `city' draws its data from a lookup table, which also gives you data for the fields listed in the `mapping` parameter. You can then leave those keys undefined. Notice that you should also specify the column representing the primary key for the table:

```
```ruby
'city' => ['source' => FakeData::SOURCE_TABLE,
           'name' => 'world_city_data',
           'idcol' => 'id',
           'mapping' => [
             'city' => 'city',
             'state_province' => 'state_province',
             'postal_code_prefix' => 'postal_code',
             'iso2' => 'country'
           ],
           'state_province' => [],
           'postal_code' => [],
           'country' => [],
         ]
```
```

You can then define the destination table, a Connection instance, and create the FakeData instance. A foreach() loop will suffice to display a given number of entries:

```
```ruby
$destTableName = 'prospects';
$conn = new Connection(include DB_CONFIG_FILE);
$fake = new FakeData($conn, $mapping);
foreach ($fake->generateData(10) as $row) {
    echo implode('|', $row) . PHP_EOL;
}
```
```

The output, for 10 rows, would look something like this:

![](bbox=[0.24, 0.56, 0.75, 0.83])