```
"company_name",
"contact_name",
"city",
"state",
"accomplishments",
"followup",
"literature_request" ));
}
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