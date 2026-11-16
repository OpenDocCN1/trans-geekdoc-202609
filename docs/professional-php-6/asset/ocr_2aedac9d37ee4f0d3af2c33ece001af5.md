# Part III: A Real-World Case Study

Moving the persistence functions (implodeQuoted, generateSqlInsert, isValid, persistWork) and persistence state (contentBase, dispatchFunctions) into PersistableObject enables Contact, ContactVisit, and WidgetUser to be implemented in a much shorter form:

```
class Contact extends PersistableObject {
    function __construct ($results, $dbh = null) {
        parent::__construct ($results, $dbh);
    }

    public function persist() {
        return $this->persistWork ("contact",
            array ( "emp_id",
                "week_start",
                "shop_calls",
                "distributor_calls",
                "engineer_calls",
                "mileage",
                "territory_worked",
                "territory_comments")) ;
    }

    public function getSqlWhere() {
        return " emp_id = "."$this->emp_id." and
            week_start = "."$this->week_start.".";
    }
}
```

```
class ContactVisit extends PersistableObject {

    function __construct ($results, $dbh = null) {
        parent::__construct ($results, $dbh);
        static $sequence = 0;
        $Sequence = $sequence + 1; // increment across class
        $this->contentBase["seq"] = $sequence;
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
    if ($this->isEmpty("week_start") == true) return false;
    if ($this->isEmpty("company_name") == true) return false;
    return true;
}
```

```
public function persist() {
    return $this->persistWork ("contact_visits",
        array ( "emp_id",
            "week_start",
            "seq",
```