

```php
$cv->persist();
$result = $this->session->getDatabaseHandle()->query("select * FROM
contact_visits WHERE emp_id = 1 and week_start = '1980-01-01'");
$this->assertEquals(1, $result->numRows());
}
```

请注意，week_start 的值选为 1980 年元旦是有原因的：

- 它不是正常周的开始，对美国人来说，正常周通常从星期日开始。
- 它在你心中格外突出，因此如果出了严重问题并且它进入了生产数据库，可以轻易地被识别为非真实联系人。

在运行测试之前，别忘了为 ContactVisit 打桩，以确保测试在正确满足测试之前能够成功 FAIL（但在语法上能执行）。以下是 contact.php 的内容：

```
class ContactVisit {
function __construct ($results) {
public function isValid() { return null; }
public function persist() { }
public function getSequence() { return null; }
}
```

## 满足测试

由于访问将按顺序进行，请使用静态变量，以便序列计数在类的所有实例之间共享。在构造函数中递增它还可确保无需更多管道代码即可覆盖所有情况。在 contact.php 中实现 ContactVisit 的构造函数：

```
class ContactVisit {
function __construct ($results, $dbh = null) {
static $sequence = 0;
$this->dbh = $dbh;
$this->contentBase = $results; // copy
$sequence = $sequence + 1; // increment across class
$this->contentBase["seq"] = $sequence;
}
```

```
public function isValid() { return null; }
public function persist() { }
public function getSequence() { return null; }
}
```

此外，请注意 ContactVisit 必须存储对数据库的引用。这是正常数据（公司名称、城市、州等）之外的内容，因此在 ContactVisit 的 `__get()` 函数的最后一个 return 中返回 ContactVisit 的状态。以下是 contact.php 中的内容：

```
function __get ($key) {
  if (array_key_exists ($key, $this->contentBase)) {
    return $this->contentBase[$key];
  }
  return $this->$key;
}
```

将所有内容整合在一起，添加一些生成所需 SQL 的函数，就大功告成了。contact.php 文件如下：

```
class ContactVisit {
  protected $contentBase = array();
  protected $dbh = null; // database handle

  function __get ($key) {
    if (array_key_exists ($key, $this->contentBase)) {
      return $this->contentBase[$key];
    }
    return $this->$key;
  }

  function __construct ($results, $dbh = null) {
    static $sequence = 0;
    $this->dbh = $dbh;
    $this->contentBase = $results; // copy
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

  private function implodeQuoted(&$values, $delimiter) {
    $sql = "";
    $flagIsFirst = true;
    foreach ($values as $value) {
      if ($flagIsFirst) {
        $flagIsFirst = false;
      } else {
        $sql .= $delimiter;
      }
      if (gettype($value) == "string") {
        $sql .= "'".$value."'";
      } else {
        $sql .= $value;
      }
    }
    return $sql;
  }

  private function generateSqlInsert($tableName, &$metas, &$values) {
    return "insert into " . $tableName .
    " (" . implode($metas, ", ") . ") " .
    " values ( " . $this->implodeQuoted($values, ", ") . ")";
  }

  public function persist() {
    if ($this->isValid() == false) return false;
    $sql = $this->generateSqlInsert("contact_visits",
    array("emp_id",
    "week_start",
    "seq",
    "company_name",
    "contact_name",
    "city",
    "state",
    "accomplishments",
    "followup",
    "literature_request"),
    array($this->emp_id,
    $this->week_start,
    $this->seq,
    $this->company_name,
    $this->contact_name,
    $this->city,
    $this->state,
    $this->accomplishments,
    $this->followup,
    $this->literature_request));
    if (DB::isError($this->dbh->query($sql))) return false;
    return true;
  }
}
```

简言之，已实现的方法如下：

- isValid() 满足你的两个有效性测试。isValid() 依赖于 isEmpty()，这只是一个方便函数。
- persist() 满足你的持久性测试。persist() 调用 generateSqlInsert()，后者根据表名、表元信息以及你想要插入的值生成 SQL INSERT 语句。generateSqlInsert() 又调用 implodeQuoted()，为字符串值添加 SQL 引号。

implodeQuoted() 和 generateSqlInsert() 均坚持数组按引用传递，而非按值传递。当然，PHP 6 的默认行为是按引用传递对象，但数组在默认情况下按值传递。

## 创建屏幕

请考虑以下名为 customer-contacts.tpl 的表单：

```
{include file="header.tpl" title="Widget World - Customer Contact"}
<h3>Customer Contact Report</h3>
<form action="customer-contacts.php" method="post">
<table border="0" width="100%">
<tr>
<td><b>Employee Name:</b></td><td>{$user->first_name} {$user->last_name}</td>
<td><b>Department:</b></td><td>{$user->department}</td>
</tr>
<tr>
<td><b>Number:</b></td><td>{$user->id}</td><td><b>Start Week:</b></td>
<td><SELECT NAME="week_start">
{html_options values=$start_weeks output=$start_weeks selected=$current_start_week}
</SELECT>
</td>
</tr>
</table>
<br><br>
<hr>
<p><font size="+1">
<b>Significant Distributors and Customers Visited:</b>
</font>
<br>
(also distributors/OEM/prospects)<p>
<table border="0">
{section name=idx loop=$max_weekly_contacts} {strip}
<tr>
<td width="20"></td>
<td><b>Company:</b></td>
<td><b>Contact:</b></td>
<td><b>City:</b></td>
<td><b>State:</b></td>
<td><b>FollowUp:</b></td>
<td><b>Literature Request:</b></td>
</tr>
<tr>
<td width="20"></td>
<td><input name="company_name_{$smarty.section.idx.index}"
size="20" maxlength="50"></td>
<td><input name="contact_name_{$smarty.section.idx.index}"
size="20" maxlength="50"></td>
<td><input name="city_{$smarty.section.idx.index}"
size="20" maxlength="50"></td>
<td><input name="state_{$smarty.section.idx.index}"
size="10" maxlength="50"></td>
<td><input name="followup_{$smarty.section.idx.index}"
size="20" maxlength="2000"></td>
<td><input name="literature_request_{$smarty.section.idx.index}"
size="20" maxlength="2000"></td>
</tr>
<tr>
<td width="20"></td>
<td colspan="7"><b>Accomplishments:</b></td>
</tr>
<tr>
<td width="20"></td>
<td colspan="7">
<TEXTAREA NAME="accomplishments_{$smarty.section.idx.index}"
ROWS=4 COLS=95></TEXTAREA><br><br>
</td>
</tr>
</table>
{/strip}{/section}
<table>
<br><hr>
<input type="hidden" name="action" value="persist_contact">
<br><br>
<center>
<input type="submit" name="submit" value=" Save " 
onclick="return checkInputs(this.form);">
</center>
</form>
{include file="footer.tpl"}
```

请注意，主循环 {section name=idx loop=$max_weekly_contacts} 会迭代并创建唯一的输入名称：company_name_{$smarty.section.idx.index}，然后对这些名称进行操作。

Smarty 提供了一个便捷的功能，可根据当前周的日期数组填充下拉框：

```
<SELECT NAME="week_start">
{html_options values=$start_weeks
output=$start_weeks selected=$current_start_week}
</SELECT>
```

你可能已经注意到，输入屏幕外观相当简陋，因为它使用的是常规 HTML，而不是像 XHTML 和 CSS 这样更严格、跨平台浏览器兼容性更好的东西。这是因为，在这个过程中，你更关心让系统运行起来而不是外观，因为定义在不久的将来可能会略有更改。在过程的后期，可以对显示进行美化。

## 喂养野兽

尽管 ContactVisits 知道如何持久化自身，但收集几周的下拉框信息，然后将所有联系人保存到数据库中，需要出人意料的大量工作。所需功能简单地放置在 customer-contacts.php 的函数中：

```
<?php
require_once ("Smarty.class.php") ;
require_once ("widgetsession.php") ;
$session = new WidgetSession(array ('phptype' => "pgsql",
'hostspec' => "localhost",
```

