```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<question text="Who should be kicked out?">
<answer id="a" text="The coach">577</answer>
<answer id="b" text="The players">53</answer>
<answer id="c" text="The board">85</answer>
</question>
```
```

The example script now counts the number of responses and returns the result in a variable, $ans_max. This variable is then used in a loop that goes through all the responses, uses a start angle as the counter in each case, and then moves it on based on the value in the response:

```
```php
$start = 0;
foreach ($sim->answer as $answer) {
...
$end = $start + 360 * intval($answer) / $ans_max;
...
$start = $end;
}
```
```

The actual components of the pie chart are now created in this loop. In the first step, the RGB numerical values are assigned random values in three variables for the red, green, and blue color values:

```
```php
$r_random = mt_rand(50, 220);
```
```

The individual pie slices are then created with the PieSector() method:

```
```php
$pdf->PieSector($pdf->getPageWidth() / 2, 140, $pdf->getPageWidth() / 3,
$start, $end);
```
```

This is also where the getPageWidth() method is used to determine the correct size for the diagram.

In the last step, the legend label for each answer is set as a MultiCell:

```
```php
$pdf->MultiCell(100, 5, $answer["text"] . ": " . $answer, 0, 'L', 0, 1, 5);
```
```

The following listing shows the complete script at a glance; the diagram follows in Figure 31.4.

```
```php
$sim = simplexml_load_file("survey.xml");

//Determine the total number of responses
$ans_max = 0;
foreach ($sim->answer as $answer) {
$ans_max += intval($answer);
}
```
```