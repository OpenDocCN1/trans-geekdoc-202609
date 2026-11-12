```
```php
$sum = 0;
$nb_of_even_numbers = 0;
	foreach ($tab as $number) {
	if($number % 2 == 0){
	$sum += $number;
	$nb_of_even_numbers++;
	}
	}
	echo $nb_of_even_numbers;
echo "<br>";
$average = $sum/$nb_of_even_numbers;
return $average;
}
$tab = [1,2,6,8,10,9,13,14,20];
echo average_of_even_numbers($tab);
```
```