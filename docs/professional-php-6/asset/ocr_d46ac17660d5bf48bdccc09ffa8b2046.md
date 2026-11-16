However, every other test sets cash_advance to zero. What happens if you remove cash_advance
from the test? It breaks! This is because PersistableObject blindly creates SQL based on every field of
the database record.

Modify the persistence test to reflect that neither cash_advance nor comments is required:

```
function testTravelExpenseWeekPersistence() {
	$this->session->getDatabaseHandle()->query("delete FROM
travel_expense_week WHERE emp_id = 1 and
week_start = '1980-01-01'"); // remove multiples

	$tvi = new TravelExpenseWeek (
	array ('emp_id' => "1",
	'week_start' => "1980-01-01",
	'territory_worked' => "Midwest",
	'mileage_rate' => "0.31"));
	$this->session->getDatabaseHandle();

	$result = $this->session->getDatabaseHandle()->query("select *
FROM travel_expense_week WHERE emp_id = 1 and week_start
= '1980-01-01'");

	$this->assertEquals(0, $result->numRows (), "pre check");
	$this->assertEquals (true, $tvi->persist (), "save");
	$result = $this->session->getDatabaseHandle()->query("select *
FROM travel_expense_week WHERE emp_id = 1 and week_start
= '1980-01-01'");
	$this->assertEquals(1, $result->numRows (), "persisted ok");
	$row = $result->fetchRow();
	$this->assertEquals (0.0, (float) $row['cash_advance'],
"cash advance default");
}
```

The default values of cash_advance are an easy fix, too. Just modify the constructor of
TravelExpenseWeek to set the default of zero and an empty string:

```
class TravelExpenseWeek extends PersistableObject {
function __construct ($results, $dbh = null) {
$this->contentMetaTable = "travel_expense_week";
$this->contentMetaOnly = array ("emp_id",
"week_start",
"comments",
"territory_worked",
"cash_advance",
"mileage_rate");

$this->contentBase['comments'] = "";
$this->contentBase['cash_advance'] = "0.0";
	parent::__construct ($results, $dbh);
}
```