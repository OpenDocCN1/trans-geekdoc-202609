```
"week_start",
"comments",
"territory_worked",
"cash_advance",
"mileage_rate"));
)
public function getSqlWhere() {
return " emp_id = ".$this->emp_id." and week_start
= ".$this->week_start."";
}
public function parse(&$request) { }
public function readWeek() { }
public function getExpenseAmount($offset, $description) { }
}
```

The functions parse, readWeek, and getExpenseAmount are required by the
TravelExpenseWeekContainerParseRequest and TravelExpenseWeekContainerWrite tests; thus,
they are simply syntactic stubs.

# Satisfying the Parse Request Test

The TravelExpenseWeekContainerParseRequest test may be a bit tricky because it involves data
manipulation. Your first order of business is to take care of the dependencies, which is part of the meta-
array road map that you were thinking about earlier. Adding this function to the TravelExpenseWeek
class in lib/expense.phpm will take care of the job:

```
public function getExpensesMetaArray () {
return array(
array('name' => 'Lodging', 'code' => 'lodging', 'data' =>
array('Lodging &amp; Hotel','Other','Tips'), 'persist' =>
array('lodging_amp_hotel', 'lodging_laundry',
'lodging_tips')),
array('name' => 'Meals', 'code' => 'meals', 'data' =>
array('Breakfast', 'Lunch &amp; Snacks',
'Dinner', 'Tips', 'Entertainment'), 'persist' =>
array('meals_breakfast', 'meals_lunch',
'meals_dinner', 'meals_tips',
'meals_entertainment')),
array('name' => 'Transportation', 'code' => 'trans', 'data' =>
array('Airfare', 'Auto Rental', 'Auto Maint./Gas',
'Local Transportation',
'Tolls/Parking'), 'persist' =>
array ('trans_airfare', 'trans_auto_rental',
'trans_auto_maint', 'trans_local',
'trans_tolls', 'trans_miles_traveled')),
array('name' => 'Miscellaneous', 'code' => 'misc', 'data' =>
array('Gifts', 'Telephone &amp; Fax', 'Supplies',
'Postage', 'Other'), 'persist' =>
array('misc_gifts', 'misc_phone',
'misc_supplies', 'misc_postage',
'misc_other')));
}
```