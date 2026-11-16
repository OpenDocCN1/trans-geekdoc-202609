
这是你的初始 index.php 文件：

```php
<?php
require_once ("Smarty.class.php"); require_once ("widgetsession.php");
$session = new WidgetSession(array(
'phptype' => "pgsql",
'hostspec' => "localhost",
'database' => "widgetworld",
'username' => "wuser",
'password' => "foobar"));
$session->Impress();
$smarty = new Smarty;
if ($_REQUEST["action"] == "login") {
$session->login($_REQUEST["login_name"],$_REQUEST["login_pass"]);
if ($session->isLoggedIn()) {
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
} else {
$smarty->assign('error', "Invalid login, try again.");
$smarty->display ("login.tpl");
exit;
}
} else {
if ($session->isLoggedIn() == true) {
$smarty->assign_by_ref("user", $session->getUserObject());
$smarty->display ("main.tpl");
exit;
}
}
$smarty->display ("login.tpl");
?>
```

屏幕的逻辑如下。如果表单的 action 变量为 login，则表示正在尝试登录，因此通过调用 $session->login() 尝试登录。正面结果通过渲染主菜单来处理。负面结果会导致设置一个错误变量，并且登录界面会再次显示给用户。

当然，如果你不是在尝试登录，则会检查 $session->isLoggedIn() 以确认会话中的登录状态。如果用户已登录，则显示主菜单屏幕。否则，会再次显示登录屏幕。

登录屏幕和主屏幕这两个界面，连同页眉和页脚，都很简单。

以下是 login.tpl 的代码：

```
{include file="header.tpl" title="Widget World Login"}
<h3>Please Login:</h3> <p>
{section name=one loop=$error}{sectionelse}
<font color="#FF0000">($error)</font><p>
{/section}
<form action="index.php" method="post">
<table border="0">
<tr>
<td width="20"></td>
<td>User:</td>
<td><input name="login_name" type="text" size="20" maxlength="50"></td>
</tr>
<tr>
<td width="20"></td>
<td>Password:</td>
<td><input name="login_pass" type="password" size="20" maxlength="50"></td>
</tr>
<tr>
<td width="20"></td>
<td></td>
<td><input type="submit" value=" Login "></td>
</tr>
</table>
<input type="hidden" name="action" value="login">
</form>
{include file="footer.tpl"}
```

## 第三部分：实际案例研究

以下是 header.tpl 的代码：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<meta HTTP-EQUIV="content-type" CONTENT="text/html; charset=ISO-8859-1">
<title>{$title|default:"no title"}</title>
</head>
<h1>Widget World</h1>
<hr><p>
```

以下是 footer.tpl 的代码：

```
<br/><br/>
<hr/>
For Widget World use only - testing environment.
</body>
</html>
```

以下是 main.tpl 的代码：

```
{include file="header.tpl" title="Widget World Menu"}
Welcome {$user->first_name} the {$user->role}!
<table border="0" cellspacing="8" cellpadding="8">
{strip}
{section name=security show=$user->isAccountant()}
<tr><td><h3>Accountant functionality goes here.</h3></td></tr>
{/section}
<tr>
<td valign="top">
<h3><a href="travel-expenses.php">New Travel Expenses</a></h3>
</td>
</tr>
<tr>
<td valign="top">
<h3><a href="customer-contacts.php">New Customer Contacts</a></h3>
</td>
</tr>
{/strip}
</table>
{include file="footer.tpl" }
```

图 19-3 展示了其外观。登录后，你将看到如图 19-4 所示的菜单。如果将 ed 的角色更改为会计（accountant），则 ed 会看到稍有不同的视图，如图 19-5 所示。

![](img/a1b732997d9cb194dceec0570dc79710_468_0.png)

图 19-3：登录屏幕

![](img/a1b732997d9cb194dceec0570dc79710_468_1.png)

图 19-4：主菜单

![](img/a1b732997d9cb194dceec0570dc79710_469_0.png)

图 19-5：Ed 的视图

恭喜！你的第一个用户故事现已完成。你利用 PHP 会话、数据库查询、PEAR::DB 和 PHPUnit 完成了大量工作，以实现确定谁在登录以及该用户应该能够做什么所需的功能，这绝非易事。

好好休息一下，享受吃饼干的时光；还有大量工作即将到来。

### 下一个用户故事

你之前的用户故事（用户故事 9：“身份验证与授权”）值 4 个点数。请记录完成这个 4 点数任务花了多少天或半天。

请回顾，本次迭代的客户联系报告包含以下内容：

- [ ] 用户故事 9：身份验证与授权，4 点数（已完成）
- [ ] 用户故事 1：客户联系报告，3 点数
- [ ] 用户故事 6：销售经理通知，3 点数
- [ ] 用户故事 8：邮件室通知，2 点数

是时候重新投入工作了。

### 客户联系需求

请回顾本章前面部分（参见图 19-1）中每周联系报告的要求。其数据要求大致如下：

```
CREATE TABLE contact_visits (
  emp_id integer NOT NULL,
  week_start date NOT NULL,
  seq integer NOT NULL,
  company_name varchar(40) default NULL,
  contact_name varchar(40) default NULL,
  city varchar(40) default NULL,
  state varchar(40) default NULL,
  accomplishments text,
  followup text,
  literature_request text
);
CREATE UNIQUE INDEX cv_pk on contact_visits (emp_id,week_start,seq);
CREATE INDEX cv_emp_id ON contact_visits (emp_id);
CREATE INDEX cv_week_start ON contact_visits (week_start);
CREATE INDEX cv_seq ON contact_visits (seq);
```

数据按周存储，与员工关联，且在包含序列列时具有唯一性。数据量可能很大。

请注意，state 字段长度为 40 个字符，以容纳非美国州份，以及加拿大和墨西哥的省份。还要注意，客户联系报告包含员工的部门，而当前用户表中尚不存在该字段。请继续添加它：

```
CREATE TABLE "user" (
id serial PRIMARY KEY,
username varchar(32) default NULL,
md5_pw varchar(32) default NULL,
first_name varchar(64) default NULL,
last_name varchar(64) default NULL,
email varchar(255) default NULL,
role char(1) NOT NULL default 's',
department varchar(40) NOT NULL default 's'
);
```

### 客户联系测试

考虑你打算如何使用客户联系数据。从这个输入屏幕来看，几乎所有表单数据都通过 Web 服务器提供，这意味着在准备将其持久化时，你需要从 WidgetSession 中获取员工 ID。

此外，在将数据写入表格之前，请考虑你需要的最低信息：id、week_start 和 sequence，使用如下的 PHPUnit 测试：

```
function testValidContactVisit() {
$cv = new ContactVisit (
array ('emp_id'
=> "1",
'seq'
=> "1",
'week_start'
=> "1980-01-01",
'company_name'
=> "test one",
'contact_name'
=> "Big One",
'city'
=> "Columbus",
'state'
=> "OH",
'accomplishments'
=> "phone call",
'followup'
=> "",
'literature_request' => ""));
$this->assertEquals(true, $cv->isValid(), "valid log");
}
```

此测试是 ContactVisit 所需的最低信息。因此，如果 emp_id、seq 和 week_start 包含任何值，则 isValid() 将返回 true。反之亦然，也应该进行相反的测试：

```
function testInvalidContactVisit() {
    $cv = new ContactVisit (
        array ('emp_id'
        => "1",
        'week_start' => "", // date required
        'company_name' => "test one",
        'contact_name' => "Big One",
        'city' => "Columbus",
        'state' => "OH",
        'accomplishments' => "phone call",
        'followup' => "",
        'literature_request' => ""));
    $this->assertEquals(false, $cv->isValid(), "invalid visit");
}
```

由于每次拜访都需要唯一的序列值，因此它们不妨自行确定顺序：

```
function testSequence() {
    $cv1 = new ContactVisit(array());
    $this->assertEquals(1, $cv1->seq);
    $cv2 = new ContactVisit(array());
    $this->assertEquals(2, $cv2->seq);
}
```

请注意，通过创建 ContactVisit，每个新 ContactVisit 的序列（seq）会自动递增，从而无需要求容器为每个实例分配唯一的序列号。

持久化仍在变动之中，但这肯定可行：

```
function testPersistence() {
    $this->session->getDatabaseHandle()->query("delete FROM
        contact_visits WHERE emp_id = 1 and week_start = '1980-01-01'");
    // remove multiples
    $cv = new ContactVisit (
        array ('emp_id' => "1",
        'week_start' => "1980-01-01",
        'seq' => 1,
        'company_name' => "test one",
        'contact_name' => "Big One",
        'city' => "Columbus",
        'state' => "OH",
        'accomplishments' => "phone call",
        'followup' => "",
        'literature_request' => ""));
    $result = $this->session->getDatabaseHandle()->query("select * FROM
        contact_visits WHERE emp_id = 1 and week_start = '1980-01-01'");
    $this->assertEquals(0, $result->numRows());
}
```
