Not a problem, because Contact is used in much the same way as ContactVisits. Create a test for contact persistence:

```
function testContactPersistence() {
    $this->session->getDatabaseHandle()->query("delete FROM contact WHERE
      emp_id = 1 and week_start = '1980-01-01'"); // remove multiples
    $c = new Contact (
    array ("emp_id" => "1",
    "week_start" => "1980-01-01",
    "shop_calls" => 2,
    "distributor_calls" => 3,
    "engineer_calls" => 4,
    "mileage" => 50,
    "territory_worked" => "Central Ohio",
    "territory_comments" => "Buckeyes are great. " ),
    $this->session->getDatabaseHandle());
    $result = $this->session->getDatabaseHandle()->query("select * FROM
      contact WHERE emp_id = 1 and week_start = '1980-01-01'");
    $this->assertEquals(0, $result->numRows());
    $c->persist();
    $result = $this->session->getDatabaseHandle()->query("select * FROM
      contact WHERE emp_id = 1 and week_start = '1980-01-01'");
    $this->assertEquals(1, $result->numRows()); }

```

Contact also shares the same scope as ContactVisits. This is a big hint, because the two classes do pretty much the same thing and share the same scope. They’re typically an easy refactoring target.

Looking deeper into the classes, you see that your hunch is correct, and that the new Contact class, and the existing ContactVisit and WidgetUser classes, contain common functionality.

As you may recall from earlier, the footprint of ContactVisit and WidgetUser is as follows:

```
class ContactVisit {
    protected $contentBase = array();
    protected $dbh = null; // database handle
    function __get ($key) {}
    function __construct($results, $dbh = null) {}
    private function isEmpty($key) {}
    public function isValid() {}
    private function implodeQuoted() {}
    private function generateSQLInsert($tableName, &$metas, &$values) {}
    public function persist() {}
}
```

class WidgetUser {

```
protected $contentBase = array();
protected $dispatchFunctions = array ("role" => "getrole");
function __construct($initdict) {}
```

```
function __get ($key) {}
```