+   13. Depending on the level of realism desired, you could also build a database table that matches postal codes to cities. Postal codes could also be randomly generated. Here is an example that generates postal codes for the UK:

```
public function getPostalCode($entry, $pattern = 1)
{
    
        return $this->alpha[random_int(0,25)]
            .$this->alpha[random_int(0,25)]
            .random_int(1, 99)
            . ' '
            .random_int(1, 9)
            .$this->alpha[random_int(0,25)]
            .$this->alpha[random_int(0,25)];
    
}
```

+   14. Fake e-mail generation can likewise use a set of seed arrays to produce random results. We could also program it to receive an existing `$entry` array, with parameters, and use those parameters to create the name portion of the address:

```
public function getEmail($entry, $params = NULL)
{
    
        $first = $entry[$params[0]] ?? $this->alpha[random_int(0,25)];
        $last = $entry[$params[1]] ?? $this->alpha[random_int(0,25)];
        return $first[0] . '.' . $last
            .'@'
            .$this->email1[array_rand($this->email1)]
            .$this->email2[array_rand($this->email2)]
            . '.'
            ."'"
            .$this->email3[array_rand($this->email3)];
    
}
```

+   15. For date generation, one approach would be to accept as arguments an existing `$entry` array, with parameters. The parameters would be an array where the first value is a start date. The second parameter would be the maximum number of days to subtract from the start date. This effectively lets you return a random date from a range. Note that we use `DateTime::sub()` to subtract a random number of days. `sub()` requires a `DateInterval` instance, which we build using `P`, the random number of days, and then `'D':`

```
public function getDate($entry, $params)
{
    
        list($fromDate, $maxDays) = $params;
        $date = new DateTime($fromDate);
        $date->sub(new DateInterval('P' . random_int(0, $maxDays) . 'D'));
        return $date->format('Y-m-d H:i:s');
    
}
```