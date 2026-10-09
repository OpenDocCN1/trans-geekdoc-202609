```
echo '1:' . $pub->getData()[1] . PHP_EOL;
},
10
);
$sub2 = new Subscriber(
'2',
function ($pub) {
echo '2:' . $pub->getData()[2] . PHP_EOL;
},
20
);
$sub3 = new Subscriber(
'3',
function ($pub) {
echo '3:' . $pub->getData()[3] . PHP_EOL;
},
99
);
```

For test purposes, attach the subscribers out of order, and call `notify()` twice:

```
$pub->attach($sub2);
$pub->attach($sub1);
$pub->attach($sub3);
$pub->notify();
$pub->notify();
```

Next, define and attach another subscriber that looks at the data for subscriber 1 and exits if it's not empty:

```
$sub4 = new Subscriber(
'4',
function ($pub) {
echo '4:' . $pub->getData()[4] . PHP_EOL;
if (!empty($pub->getData()[1]))
die('1 is set ... halting execution');
},
25
);
$pub->attach($sub4);
$pub->notify();
```