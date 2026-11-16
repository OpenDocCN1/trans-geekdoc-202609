```
$result = $this->session->getDatabaseHandle()->query("select * FROM
travel_expense_item WHERE emp_id = 1 and
expense_date = '1980-01-01'");
$this->assertEquals(1, $result->numRows());
}
```

Remember to connect to your testing database when running these tests. The last thing you want is to accidentally torch production data with an errant DELETE statement.

Stub out your travel expense item in the new file, lib/expense.phpm:

```
class TravelExpenseItem {
public function isValid() { }
public function persist() { }
}
```

Ensure that the tests run (and fail), and then get to work satisfying them.

Using ContactVisit as a template, it’s surprisingly easy:

```
class TravelExpenseItem extends PersistableObject {
function __construct($results, $dbh = null) {
parent::__construct($results, $dbh);
}
}
```

```
private function isEmpty($key) {
if (array_key_exists($key, $this->contentBase) == false) return true;
if ($this->contentBase[$key] == null) return true;
if ($this->contentBase[$key] == "") return true;
return false;
}
```

```
public function isValid() {
if ($this->isEmpty("emp_id") == true) return false;
if ($this->isEmpty("expense_date") == true) return false;
if ($this->isEmpty("description") == true) return false;
if ($this->isEmpty("amount") == true) return false;
return true;
}
public function persist() {
return $this->persistWork (
"travel_expense_item",
array ( "emp_id",
"expense_date",
"description",
"amount" ));
}
public function getSqlWhere() {
return " emp_id = ".$this->emp_id." and expense_date =
".".$this->expense_date."" and description =
".".$this->description.""";
}
}
```