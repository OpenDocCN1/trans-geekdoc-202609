
现在代码更清晰了，很明显你的逻辑可以重构如下：

```
if (array_key_exists("action", $_REQUEST)) {
    switch ($_REQUEST["action"]) {
        case "login":
            $session->login($_REQUEST["login_name"], $_REQUEST["login_pass"]);
            break;
        case "logout":
            $session->logout();
            break;
    }
}
displaySmartyPage($smarty, $session, "main.tpl");
```

因为displaySmartyPage()函数只被调用一次，你现在可能能明白为什么之前把代码重构到displaySmartyPage()函数中了。

既然displaySmartyPage()函数代码已不再必要，你要撤销之前的“提取方法”重构，改用“内联方法”技术（也见于Martin Fowler的《重构》）将其重构回去。这完全相反：

```
<?php
require_once ("lib/common.php");
if (array_key_exists("action", $_REQUEST)) {
    switch ($_REQUEST["action"]) {
        case "login":
            $session->login($_REQUEST["login_name"], $_REQUEST["login_pass"]);
            break;
        case "logout":
            $session->logout();
            break;
    }
}
if ($_session->isLoggedIn()) {
    $smarty->assign_by_ref("user", $_session->getUserObject());
}
$smarty->display ("main.tpl");
} else {
    if (array_key_exists("login_name", $_REQUEST)) {
        $smarty->assign('error', "Invalid login, try again.");
    }
    $smarty->display ("login.tpl");
}
?>
```

只需付出一点努力，你就显著降低了复杂度，移除了多余的Smarty调用，并将总行数减少了三分之一以上。

正如你所见，降低复杂度可以带来一些惊人的节省，代码也更易于阅读和理解。当然，你应当通过践行“一次且仅一次”规则来避免陷入代码债。如果有选择，保持解决方案简单，不要害怕移除不需要的功能。

## 完成迭代

牢记你新学到的重构技巧，处理剩下的用户故事时，着眼于消除重复并使代码更简单。

## 用户故事14：切换周时调用前一周

调用状态并不困难，因为ContactVisit状态几乎就是恳求这样做。你通过将以下函数添加到customer-contacts.php中，很快就完成了一半：

```
function gatherContactVisits ($dbh, $emp_id) {
	$result = $dbh->query ("select * from contact_visits where
		emp_id = ".$emp_id." and week_start = 
		'".getCurrentStartWeek()."' order by seq");
	if (DB::isError($result)) {
		return array();
	}
	$visits = array();
	while ($row =& $result->fetchRow()) {
		array_push ($visits, new ContactVisit($row));
	}
	return $visits;
}
```

在调用gatherContactVisits()函数时应该采取“懒加载”策略，因为从数据库调用ContactVisits()的操作并非每次都需要（例如，在保存ContactVisits()时）。

现在，按引用将联系访问数据分配给ContactVisits，并在customer-contacts.tpl中像这样为显示调用它：

```
<input name="company_name_${smarty.section.idx.index}" size="20"
	maxlength="50" value="${contactVisits[idx]->company_name}">
```

你已经准备好一切，除了当下拉菜单中的周发生变化时重新加载。这里有一个小技巧：下拉菜单通常不会触发表单提交，但在这种情况下你需要强制提交。

为了强制提交，你创建一个带有week_start值的隐藏表单。当日期发生变化时，调用JavaScript函数reload，它会将week_start填充为所选内容。然后，用一个新的action“提交”它：

```
{literal}
<SCRIPT TYPE="text/javascript">
<!--
function reload () {
	window.document.forms[0].week_start.value =
		window.document.forms[1].week_start.value // hidden form
	window.document.forms[0].submit(); // hidden form
}
// -->
</SCRIPT>
</literal>
```

### 客户联系报告

```
<form action="customer-contacts.php" method="post">
<input type="hidden" name="action" value="reload_contact">
<input type="hidden" name="week_start" value="">
</form>
```

```
<form action="customer-contacts.php" method="post">
<table border="0" width="100%">
<tr>
<td><b>Employee Name:</b></td><td>{$user->first_name} {$user->last_name}</td>
<td><b>Department:</b></td><td>{$user->department}</td>
</tr>
<tr>
<td><b>Number:</b></td><td>{$user->id}</td>
<td><b>Start Week:</b></td>
<td>
<SELECT NAME="week_start" onchange="reload()">
{html_options values=$start_weeks output=$start_weeks
selected=$current_start_week)
</SELECT>
</td>
</tr>
</table><br><hr>
```

## 用户故事15：客户联系报告中的每周项目

需要关注的要素包括店铺来电数、工程师来电数、分销商来电数、约束里程、工作区域和区域评论。所有这些都按周发生。

要意识到，你正在查看联系访问与新结构Contact之间的多对一关系：

```
CREATE TABLE contact (
  emp_id integer NOT NULL default '0',
  week_start date NOT NULL,
  shop_calls integer default NULL,
  distributor_calls integer default NULL,
  engineer_calls integer default NULL,
  mileage decimal(9,2) default NULL,
  territory_worked varchar(60) default NULL,
  territory_comments text
);
CREATE UNIQUE INDEX co_pk on contact (emp_id, week_start);
CREATE INDEX co_emp_id ON contact (emp_id);
CREATE INDEX co_week_start ON contact (week_start);
```

这不是问题，因为Contact的用法与ContactVisits大致相同。为联系持久性创建测试：

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

Contact还与ContactVisits共享相同的作用域。这是一个重要提示，因为这两个类做的事情几乎一样并且共享相同的作用域。它们通常是轻松的重构目标。

更深入地查看这些类，你会发现你的直觉是正确的，即新的Contact类以及现有的ContactVisit和WidgetUser类包含共同功能。

正如你之前可能记得的，ContactVisit和WidgetUser的结构如下：

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

class WidgetUser {
    protected $contentBase = array();
    protected $dispatchFunctions = array ("role" => "getrole");
    function __construct($initdict) {}

    function __get ($key) {}

    function __set ($key, $value) {
    public function getRole() {}
    public function isSalesPerson() {}
    public function isSalesManager() {}
    public function isAccountant() {}
}
```

这是使用“提取类”（参见《重构》）重构来整合代码的绝佳用例。整合将大量持久性功能上移到一个名为PersistableObject的新类中：

```
class PersistableObject {
protected $contentBase = array();
protected $dbh = null; // database handle
protected $dispatchFunctions = array ("role" => "getrole");

function __get ($key) {
// dispatch by function first
if (array_key_exists ($key, $this->dispatchFunctions)) {
$funcname = $this->dispatchFunctions[$key];
return $this->$funcname();
}

// then state
if (array_key_exists ($key, $this->contentBase)) {
return $this->contentBase[$key];
}

// then self
return $this->$key;
}

function __construct ($results, $dbh = null) {
$this->dbh = $dbh;
if ($results <> null) {
$this->contentBase = $results; // copy
}
}

public function implodeQuoted (&$values, $delimiter) {
$sql = "";
$flagIsFirst = true;
foreach ($values as $value) {
if ($flagIsFirst) {
$flagIsFirst = false;
} else {
$sql .= $delimiter;
}
if (gettype ($value) == "string") {
$sql .= "'".$value."'";
} else {
$sql .= $value;
}
}
}
```
