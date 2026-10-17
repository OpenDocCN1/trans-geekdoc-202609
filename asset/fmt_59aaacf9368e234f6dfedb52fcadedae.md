
所有重复行都已打印出来，用户可以选择如何处理这些数据。如果你进入此应用程序的 `index.php` 页面并尝试输入两个相同电话号码的票，就可以看到操作演示。图13-6 提供了一个示例。

# 348 第四部分：并不简单的应用程序

![](img/245156cc770929860a3ede93c01f9981_376_0.png)

图13-6：更新客户信息 当工作人员对问题输入更新时，该步骤存储在历史记录表中。如果条目是“公共”，将通过电子邮件向用户发送更新；否则，没有电子邮件。

注意这个有趣的查询。这里的插入包含一个语句。这个 select 实际上获取与变量 `$source` 相关的 `source_id`。插入的其他信息都来自变量。

```php
function history_entry
($problem_id="",$entry_type_id="",$entered_by="",
$source="",$notes="")
{
	if (empty($problem_id)) { return FALSE; }
	if (empty($entered_by)) { $entered_by = "customer"; }
	// 在历史记录表中创建记录，从 sources 表获取来源的 ID 值。
	$query = "insert into history
(problem_id,entry_type_id,entered_by,source_id,notes)
	select '$problem_id',$entry_type_id,'entered_by',
```

## 第13章：问题跟踪系统

```php
source_id, '$notes'
from sources where source = '$source'
```

```php
$result = safe_query($query);
if ($result)
{
    // 获取新历史记录的 ID 值
    // （由 MySQL 自动分配）。
    $entry_id = mysql_insert_id();
    // 获取打开此调用的客户的电子邮件地址
    // 如果这是一个公共历史
    // 条目，并且电子邮件地址
    // 不为空
    $cresult = safe_query("select c.email
from problems p, customers c, history h, entry_types et
where h.entry_id = $entry_id
and et.entry_type = h.entry_type_id
and et.entry_type = 'public'
and h.problem_id = p.problem_id
and p.customer_id = c.customer_id
and c.email != '' and c.email is not null");
    if ($cresult && mysql_num_rows($cresult))
    {
        // 有有效的电子邮件地址 - 使用它来
        // 通知客户调用记录
        // 已更新。
        list($email) = mysql_fetch_array($cresult);
        notify_customer($problem_id,$email,$notes);
    }
}
// 返回新历史记录创建的结果
return $result;
}
```

## NOTIFY_CUSTOMER() 此函数构造电子邮件并发送它。

```php
function notify_customer ($problem_id="", $email="", $notes="",
$problem_code="")
```

# 350 第四部分：并不简单的应用程序

```php
// Apache 全局变量 $SERVER_NAME 是我们运行的
// 服务器的名称，减去任何端口号。
$SERVER_NAME:
```

```php
// 从 $notes 中移除 HTML 标签和反斜杠。
$notes = stripslashes(cleanup_text($notes));
```

```php
if (empty($problem_code))
{
    $result = safe_query("select problem_code from
problems
where problem_id = $problem_id
");
    $problem_code = mysql_result($result,0);
    if (empty($problem_code))
    {
        $problem_code = create_problem_code();
        safe_query("update problem_code
set $problem_code = '$problem_code'
where problem_id = $problem_id
");
    }
}
```

```php
// 构建调用 problem_status.php 的绝对 URL
// 以检查此问题
$problem_url =
regular_url="$problem_status.php?problem_code=$problem_code";
```

```php
// 设置邮件正文
$msgtext = <<<EOQ
问题更新：

$notes

你可以检查此问题的当前状态

$problem_url

感谢你的耐心。

EOQ
```

```php
// 设置邮件标头
$headers = "From: webmaster@".$SERVER_NAME."\n"
"Reply-To: webmaster@".$SERVER_NAME."\n"
"X-Mailer: PHP/".phpversion().";
```

## 第 13 章：问题跟踪系统 351

```php
// 发送邮件
return mail($email, "Problem Update", $mtext, $headers);
```

PHP 将能够找到 sendmail 或另一个符合 SMTP 标准的邮件服务器以便此工作。如果你遇到问题，请检查你的 `php.ini` 文件。

![](img/245156cc770929860a3ede93c01f9981_379_0.png)

`STATUS_CHANGE()` 问题的状态将是“开启”、“已关闭”或“待处理”。如果状态发生了变化，你将希望标记出确切的变化并记录类似“状态由 John 修改为关闭”的内容。该变化应该记录在历史表中。

```php
function status_change($problem_id="")
{
    $new_status_id="";
    $old_status_id="";
    $entered_by="customer";
    if (empty($problem_id) || empty($new_status_id))
    {
        $old_status_id = $new_status_id;
        return;
    }
    if (empty($entered_by)) $entered_by = "customer";
```

```php
// 获取 entry_type 'public' 的 ID，并构建
// 一个包含新状态值的字符串，以及
// 执行更改的工作职人员的真实姓名，
// 或者在没有找到匹配职职人员时使用 $entered_by 的值，
// 例如，如果工作人员 Joe Blow
// 关闭了电话，notes 字段将设置为
// “状态由 Joe Blow 设置为已关闭”。如果客户
// 重新开启了电话，notes 将设置为
// “状态由客户 设置为重新开启”。
```

```php
// 所有这些都取决于 $new_status_id 中的值
// 是否是 status 表中记录的有效 ID。
$query = "select et.entry_type_id
```

# 352 第四部分：并不简单的应用程序

```php
. concat('Status set to '
  . ns.status
  . ' by '
  . ifull(t.staff_name,'entered_by')
) as notes
  from entry_types et, status ns
left join staff on t.username = 'entered_by'
where et.entry_type = 'public'
and ns.status_id = new_status_id
  ':'
$result = safe_query($query);
if ($result) {

  // new_status_id 是一个有效的状态 ID - 使用
  // history_entry() 在历史表中创建一个记录，
  // 记录状态变化，并发送邮件通知
  // 用户。
  list($entry_type_id, $notes) = mysql_fetch_array($result);
  history_entry($problem_id, $entry_type_id, $entered_by,
    'program', $notes);

}
```

**`DISPLAY_CALL_LIST()`** 是另一个便利函数。它打印带有表头行的查询结果。

```php
function display_call_list($query="",$subtitle="Call List")
{
  $script="edit_problem.php"

  if ($query == "") { return; }
  $result = safe_query($query);
  if (!$result) { return; }

  $calls = 0;
  while ($row = mysql_fetch_array($result))
  {
    if ($calls == 0) {

// 我们只想打印一次表头，
      // 并且只有当至少有一行时
      // 在处理结果集的第一行时
      // 执行此操作。
```

## 第 13 章：问题跟踪系统

```php
print subtitle($subtitle);
```

```php
print start_table();
```

```php
print table_row(
  "<b>Problem #</th>",
  "<b>Date</th>",
  "<b>Customer</th>",
  "<b>Problem</th>",
  "<b>Source</th>",
  "<b>Status</th>"
);
$calls++;
```

```php
// 输出关于电话的信息
```

**`CREATE_PROBLEM_CODE()`** 此函数创建一个唯一的且高度随机的 8 字符代码。

```php
function create_problem_code()
{
  return substr(md5(uniqid())),0,8);
}
```

## 脚本

这些是通过 URL 和 include 调用的页面。

## CALL_ENTRY.PHP

此页的作用类似于 call_entry_form.php，稍后会讨论。记住，此表单可能由已登录的职人员访问。注意职人员应该从 staff.php 页面开始登录。或者，你可能想通过副本来确定职人员。

```php
$staff_id = $_SESSION['staff_id'];
if ($staff_id) {
    $entered_by = $staff_id;
}
```

```php
$customer_id = $_GET['customer_id'];
if ($customer_id) {
    $query = "select * from customers where customer_id = $customer_id";
    $result = safe_query($query);
    if ($result) {
        $customer = mysql_fetch_array($result);
    }
}
```

```php
$problem_id = $_GET['problem_id'];
if ($problem_id) {
    $query = "select * from problems where problem_id = $problem_id";
    $result = safe_query($query);
    if ($result) {
        $problem = mysql_fetch_array($result);
    }
}
```

```php
$status_id = $_POST['status_id'];
if ($status_id) {
    $query = "update problems set status_id = $status_id where problem_id = $problem_id";
    safe_query($query);
}
```

```php
$notes = $_POST['notes'];
if ($notes) {
    $query = "update problems set notes = '$notes' where problem_id = $problem_id";
    safe_query($query);
}
```

```php
$note_id = $_POST['note_id'];
if ($note_id) {
    $query = "update problem_notes set notes = '$notes' where note_id = $note_id";
    safe_query($query);
}
```

```php
$new_status = $_POST['new_status'];
if ($new_status) {
    $query = "update problems set status_id = $new_status where problem_id = $problem_id";
    safe_query($query);
}
```

```php
$notes = $_POST['notes'];
if ($notes && $new_status) {
    $query = "insert into problem_notes (problem_id, status_id, entered_by, date) values ($problem_id, $new_status, '$entered_by', '$notes', now())";
    safe_query($query);
}
```

## CALL_FORM.PHP

此页是向问题添加新电话的表单。将在下一节讨论。

```php
$problem_id = $_GET['problem_id'];
if ($problem_id) {
    $query = "select * from problems where problem_id = $problem_id";
    $result = safe_query($query);
    if ($result) {
        $problem = mysql_fetch_array($result);
    }
}
```

```php
$customer_id = $problem['customer_id'];
$notes = $_POST['notes'];
$status_id = $_POST['status_id'];
if ($notes && $status_id) {
    $query = "insert into problem_notes (problem_id, status_id, entered_by, notes, date) values ($problem_id, $status_id, '$entered_by', '$notes', now())";
    safe_query($query);
}
```

## EDIT_PROBLEM.PHP

此页是编辑现有问题的表单。将在下一节之后的章节讨论。

```php
$problem_id = $_GET['problem_id'];
if ($problem_id) {
    $query = "select * from problems where problem_id = $problem_id";
    $result = safe_query($query);
    if ($result) {
        $problem = mysql_fetch_array($result);
    }
}
```
