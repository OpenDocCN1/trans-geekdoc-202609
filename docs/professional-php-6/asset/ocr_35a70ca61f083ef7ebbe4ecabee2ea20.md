```
public function persist() {
    if (parent::persist() == false) return false;
    // persist each item to the database
    foreach ($this->items as $item) {
        if ($item->persist() == false) return false;
    }
    return true;
}
public function getSqlWhere() {
    return "emp_id = ".$this->emp_id." and week_start = "."'".$this->week_start."'";
}
public function getExpensesMetaArray () {
    // content removed for brevity
}
public function getWeekArray() {
    // content removed for brevity
}
public function addDays($start, $days) {
    // content removed for brevity
}
public function parse (&$request) {
    // content removed for brevity
}
public function readWeek() {
    // content removed for brevity
}
public function getExpenseAmount($offset, $description) {
    // content removed for brevity
}
}
```

Note that TravelExpenseWeek overrides the PersistableObject->persist() function. However, it first calls PersistableObject->persist() and then persists every TravelExpenseItem that it is holding. Remember that because the logic behind an insert/update/delete is in PersistableObject->persistWork(), it continues to work, and all you need to do is remember to implement the getSqlWhere function in your concrete classes such as TravelExpenseWeek. The tests are still passing? Good job, but not so fast, considering that a cash advance is not required (as shown in the validity test):

```
function testValidTravelExpenseWeek() {
    $tvi = new TravelExpenseWeek (
        array ('emp_id' => "1",
        'week_start' => "1980-01-01",
        'comments' => "comment",
        'mileage_rate' => "0.31",
        'territory_worked' => "Midwest" ));
    $this->assertEquals(true, $tvi->isValid(), "valid expense");
}
```