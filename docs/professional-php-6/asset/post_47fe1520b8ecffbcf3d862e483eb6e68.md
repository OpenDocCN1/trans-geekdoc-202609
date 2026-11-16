
}
return $sql;
}

public function generateSqlInsert ($tableName, &$metas, &$values) {
    return " insert into ".$tableName.
    " ( ".implode ($metas, ", ")." ) ".
    " values ( ".$this->implodeQuoted ($values, ", ")." ) ";
}

public function generateSqlUpdate ($tableName, &$metas, &$values) {
    $sql = " update ".$tableName." set ";
    for ($i=0; $i<count($metas); $i++) {
        $sql .= $metas[$i]." = ".$values[$i].", ";
    }
    return $sql;
}

public function generateSqlDelete ($tableName) {
    return " delete from ".$tableName." where ".$this->getSqlWhere();
}
```

```
// note: should be implemented by concrete classes
public function getSqlWhere() {
    return "";
}
```

```
public function isValid() {
    return true;
}

public function persistWork ($tablename, $meta) {
    if ($this->isValid() == false) return false;
    $values = array();
    foreach ($meta as $mvalue) {
        array_push ($values, $this->$mvalue);
    }
```

```
if (strlen($this->getSqlWhere()) > 0) {
    $sql = $this->generateSqlDelete ($tablename);
    $this->dbh->query($sql);
}
```

```
$sql = $this->generateSqlInsert ($tablename, $meta, $values);
if (DB::isError ($this->dbh->query($sql))) return false;
return true;
} }
```

You may have noticed that the addition of generateSqlUpdate and generateSqlDelete enables PersistableObject to respectively update and delete itself in the database. Of course, both of these functions require a SQL WHERE clause so that not every record in the table is updated or deleted. This is why child classes (such as ContactVisit) have the responsibility of defining what makes them unique; they do this by implementing the getSqlWhere function.

## Part III: A Real-World Case Study

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
        return " emp_id = ".$this->emp_id." and
            week_start = ".$this->week_start."";
    }
}
```

```
class ContactVisit extends PersistableObject {

    function __construct ($results, $dbh = null) {
        parent::__construct ($results, $dbh);
        static $sequence = 0;
        $sequence = $sequence + 1; // increment across class
        $this->contentBase["seq"] = $sequence;
    }

    private function isEmpty($key) {
        if (array_key_exists($key, $this->contentBase) == false) return true;
        if ($this->contentBase[$key] == null) return true;
        if ($this->contentBase[$key] == "") return true;
        return false;
    }

    public function isValid() {
        if ($this->isEmpty("emp_id") == true) return false;
        if ($this->isEmpty("week_start") == true) return false;
        if ($this->isEmpty("company_name") == true) return false;
        return true;
    }

    public function persist() {
        return $this->persistWork ("contact_visits",
            array ( "emp_id",
                "week_start",
                "seq",
                "company_name",
                "contact_name",
                "city",
                "state",
                "accomplishments",
                "followup",
                "literature_request" ));
    }
}
```

```
class WidgetUser extends PersistableObject {
function __construct($initdict) {
parent::__construct($initdict);
$this->dispatchFunctions = array ("role" => "getrole");
$this->contentBase = $initdict; // copy
}
public function getRole() {
switch ($this->contentBase["role"]) {
case "s": return ("Sales Person");
case "m": return ("Sales Manager");
case "a": return ("Accountant");
default: return ("");
}
}
public function isSalesPerson() {
if ($this->contentBase["role"] == "s") return true;
return false;
}
public function isSalesManager() {
if ($this->contentBase["role"] == "m") return true;
return false;
}
public function isAccountant() {
if ($this->contentBase["role"] == "a") return true;
return false;
}
}
```

Boy, it sure is great to have all those unit tests to indicate when something goes wrong. One obstacle you’ll face is deciding how your target classes are used and how they differ from one another. For example, Contact and ContactVisit are subtly different in that you persist only valid ContactVisits, but there is always a possibly empty (but still instantiated) Contact.

In addition, notice that Contact implements the getSqlWhere function so that it can be deleted and updated. However, remember that ContactVisit is deleted before insertions take place, and WidgetUser is only persisted to the database, thus not requiring it to implement the getSqlWhere function.

However, the differences between Contact and ContactVisits have less to do with the classes themselves than with the business rules and the environment in which they exist. Therefore, even though your classes are starting to consolidate and share code, their respective unit tests should continue to test individual class diversity.

Now customer-contacts.tpl needs a new section in order to display the new Contact information:

```
<table border="0">
<tr>
<td>Number of Shop Calls:</td>
<td><input name="shop_calls" size="7" maxlength="17"
value="<?=$contact->shop_calls?>"></td>
<td width="20"></td>
<td>Number of Engineer Calls:</td>
<td><input name="engineer_calls" size="7" maxlength="17"
value="<?=$contact->engineer_calls?>">
</td>
</tr>
<tr>
<td>Number of Distributor Calls:</td>
<td><input name="distributor_calls" size="7" maxlength="17"
value="<?=$contact->distributor_calls?>"></td>
<td width="20"></td>
<td>Approximate Mileage:</td>
<td><input name="mileage" size="7" maxlength="17"
value="<?=$contact->mileage?>"></td>
</tr>
<tr>
<td>Territory Worked:</td>
<td colspan="2"><input name="territory_worked"
value="<?=$contact->territory_worked?>"></td>
</tr>
<tr>
<td colspan="7">
Territory Comments:<br>
<TEXTAREA NAME="territory_comments" ROWS=4 COLS=95>
<?=$contact->territory_comments?>
</TEXTAREA>
</td>
</tr>
</table>
```

Add these new support functions to customer-contacts.php in order to read and save the Contact information:

```
function persistContact (&$dbh, $emp_id) {
    $c = new Contact (
    array ("emp_id" => $emp_id,
    "week_start" => getCurrentStartWeek(),
    "shop_calls" => $_REQUEST["shop_calls"],
    "distributor_calls" => $_REQUEST["distributor_calls"],
    "engineer_calls" => $_REQUEST["engineer_calls"],
    "mileage" => $_REQUEST["mileage"],
    "territory_worked" => $_REQUEST["territory_worked"],
    "territory_comments" => $_REQUEST["territory_comments"]),
    $dbh);
    $c->persist();
}
function gatherContact (&$dbh, $emp_id) {
    $result = $dbh->query ("select * from contact where
       emp_id = ".$emp_id." and week_start =
       ".getCurrentStartWeek()."");
    if (DB::isError($result)) return array();
    return new Contact ($result->fetchRow());
}
$user = $session->getUserObject();
// display
if ($_REQUEST["action"] != "persist_contact") {
   $smarty->assign_by_ref ("user", $user);
   $smarty->assign_by_ref ("contact", gatherContact (
      $session->getDatabaseHandle(), $user->id));
   $smarty->assign_by_ref ("contactVisits", gatherContactVisits (
      $session->getDatabaseHandle(), $user->id));
   $smarty->assign('start_weeks', getStartWeeks());
   $smarty->assign('current_start_week', getCurrentStartWeek());
   $smarty->assign('max_weekly_contacts', GLOBALS['max-weekly-contacts']);
   $smarty->display('customer-contacts.tpl');
   exit;
}
// persist contact visits
require_once ("lib/contact.php");
persistContact ($session->getDatabaseHandle(), $user->id);
persistContactVisits ($session->getDatabaseHandle(), $user->id);
```

Figure 19-7 shows the results of your hard work.

![](img/a1b732997d9cb194dceec0570dc79710_496_0.png)

Figure 19-7: Adding per-week items to the Customer Contact Report t
