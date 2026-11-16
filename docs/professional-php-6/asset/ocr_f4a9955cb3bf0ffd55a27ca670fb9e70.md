Put it all together and you end up with the rewritten class. It's not that different. Things are just moved around a bit:

```
class TravelExpenseItem extends PersistableObject {
    protected $contentMetaTable = null;
    protected $contentMetaOnly = null;
    function __construct ($results, $dbh = null) {
        $this->contentMetaTable = "travel_expense_item";
        $this->contentMetaOnly = array ( "emp_id",
            "expense_date",
            "description",
            "amount");
        $content = array();
        foreach ($this->contentMetaOnly as $key) {
            if (array_key_exists($key, $results))
                $content[$key] = $results[$key];
        }
        parent::__construct ($content, $dbh);
    }
    public function isValid() {
        if ($this->isEmpty("emp_id") == true) return false;
        if ($this->isEmpty("expense_date") == true) return false;
        if ($this->isEmpty("description") == true) return false;
        if ($this->isEmpty("amount") == true) return false;
        return true;
    }
    public function getSqlWhere() {
        return " emp_id = " .$this->emp_id. " and expense_date
        = " .$this->expense_date." ' and description = " .$this->description."'";
    }
    public function persist() {
        return $this->persistWork (
            $this->contentMetaTable,
            $this->contentMetaOnly);
    }
}
```

In this case, you check whether what is being passed in via the constructor is what you're looking for. Repair the last remaining TravelExpenseWeek test and then refactor.

The TravelExpenseWeek write takes significantly less work, considering that each TravelExpenseItem already knows how to persist itself. All you need to do is call the persist() function of each one.

Simply add the small loop at the end of your persistence function of TravelExpenseWeek in lib/expense.phpm:

```
public function persist() {
    $this->persistWork ("travel_expense_week",
        array("emp_id",
            "week_start",
            "comments",
            "territory_worked",
```