

```php
);
if (strpos($problem_url, '/staff') != FALSE)
    $problem_url = str_replace('/staff', '', $problem_url);

// set the body of the email
$msgtext = <<<EOQ

Problem Update:

$notes

You can check the current status of this problem at

$problem_url

Thanks for your patience.

EOQ;

// set the headers of the email
// the Apache variable $_SERVER['SERVER_NAME'] is the name
// of the server we're running on, minus any port number.

$headers = 'From: webmaster@.' . $_SERVER['SERVER_NAME'] . "\n"
    . 'Reply-To: webmaster@.' . $_SERVER['SERVER_NAME'] . "\n"
    . 'X-Mailer: PHP/' . phpversion()
    . 'Bcc: webmaster@.' . $_SERVER['SERVER_NAME'] . "\n"
    ;

// send the email
return mail($email, 'Problem Update', $msgtext, $headers);
}
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_507_0.png)

要使此功能正常工作，PHP 必须能够找到 sendmail 或另一个符合 SMTP 标准的邮件服务器。如果遇到问题，请检查您的 php.ini 文件。

## status_change()

问题的状态通常类似于 "open"、"closed" 或 "pending"。如果发生变化，您需要标记确切的变更，并记录类似 "Status changed to closed by John" 的内容。变更应记录在历史表中。

```
function status_change($problem_id=NULL
  , $entered_by='customer'
  , $new_status_id=NULL
  , $old_status_id=NULL
)
{
  $error = NULL;
  if (empty($problem_id))
  {
    $error = 'No problem ID supplied for status change';
  }
  elseif (empty($new_status_id))
  {
    $error = 'No new status ID supplied for status change';
  }
  elseif (!($new_status = status($new_status_id)))
  {
    $error = "New status ID $new_status_id is not valid.";
  }

  if ($error)
  {
    user_error($error, E_USER_WARNING);
    return FALSE;
  }

  // just return if no change - not an error condition,
  // just a no-op
  if ($old_status_id == $new_status_id)
  {
    return TRUE;
  }

  if (empty($entered_by)) { $entered_by = 'customer'; }

  // get the ID of the entry_type 'public', and construct
  // a string containing the new status value and either
  // the real name of the staff member who made the change,
  // or the value of $entered_by if no matching staff
  // member is found. for example, if the staff member Joe Blow
  // closes a call, the notes field will be set to
  // 'Status set to Closed by Joe Blow'. if a customer
  // re-opens a call, notes will be set to
  // 'Status set to Re-opened by customer'.

  $entry_type_id = entry_type_id('public');
  $notes = "Status set to $new_status by ";
  if ($entered_by != 'customer' && isset($GLOBALS['staff_name']))
  {
      $notes .= $GLOBALS['staff_name'];
  }
  else
  {
      $notes .= $entered_by;
  }

  history_entry($problem_id, $entry_type_id, $entered_by,
      'program', $notes);
}
```

## create_problem_code()

此函数创建一个唯一且高度随机的 8 字符字母数字代码。

```
function create_problem_code()
{
    return substr(md5(uniqid(rand())),0,8);
}
```

## 脚本

以下是由 URL 和 include 语句实际调用的页面。

## problem.php

此页面几乎不做其他事情，只是调用 enter_problem() 或 update_problem() 函数之一。

```
require_once('header.php');

$params = $_REQUEST;
$params['entered_by'] = 'customer';
$params['source'] = 'web';

if (empty($params['problem_code']))
{
    enter_problem($params);
}
else
{
 update_problem($params);
}
```

## problem_entry_form.php

此表单主要调用 /book/functions/ 文件夹中的函数。它打印图 13-1 所示的表单，并确定表单中的默认信息。call_entry.php 页面将包含此页面。

此脚本有趣的地方在于它使用模板类来定义生成的 HTML 文档的外观。变量 `$tpl` 被定义为 `template_object()`：

```
$tpl = template_object();
```

然后它加载一个 HTML 模板（problem_entry.html），该模板在其代码中包含几个命名变量。

在需要将动态信息写入 HTML 文档时，这些命名变量非常有用。向命名块写入内容的一般过程如下：

```
$tpl->setCurrentBlock('block_name');
$tpl->setVariable('template_variable_name',$local_variable_name);
$tpl->parseCurrentBlock();
```

此策略使您能够将通过编程确定的值（通常来自数据库查找）写入模板，并让模板应用标准格式。它使您免受格式问题的困扰，而格式问题可能会带来无穷麻烦。完整列表如下：

```
function problem_entry_form(&$params)
{
 global $default_page_title;

 $tpl = template_object();

 if ($tpl->loadTemplatefile('problem_entry.html') == FALSE)
 {
 user_error(
 'Could not load problem entry template'
 , E_USER_ERROR
 );
 }
 if (!empty($params['error_messages']))
 {
     foreach ((array)$params['error_messages'] as $error_message)
     {
         $tpl->setCurrentBlock('error_messages');
         $tpl->setVariable('error_message',$error_message);
         $tpl->parseCurrentBlock();
     }
 }

 if (!empty($params['dup_results']))
 {
     foreach ((array)$params['dup_results'] as $result)
     {
         $tpl->setCurrentBlock('dup_row');
         foreach ($result as $f => $v)
             $tpl->setVariable("dup_$f", $v);
         $tpl->parseCurrentBlock();
     }
 }

 $tpl->setCurrentBlock('problem_entry_form');
 $tpl->setVariable($params);
 $tpl->setVariable('form_action', $_SERVER['PHP_SELF']);
 $tpl->parseCurrentBlock();

 // actually display something, finally...
 print start_page($default_page_title.': Enter New Report');
 $tpl->show();
 print end_page();
}
```

表单将提交到调用它的页面。该页面随后会调用接下来将讨论的 write_customer() 函数。

## write_customer.php

这个函数很长，虽然并不特别复杂。我们会在相关部分出现时说明有趣的地方。了解此函数可以完成的各种操作，最简单的方法是直接查看它。

此页面在很大程度上是一系列嵌套的 if...else 语句。最简单的情况是：客户记录（由 customer_id 标识）的全部或部分已存在于数据库中，并且表单中输入的信息与数据库中的内容不冲突。如果是这种情况，我们只需获取客户信息并继续。

当表单中输入的电子邮件和/或电话号码匹配多条记录，或者单条记录匹配但在其他方面与数据库中的内容不同时，就会出现更复杂的情况。在此过程中，将向客户显示所有匹配的记录，并允许其采取以下几种操作之一：

- 创建新记录
- 选择一条现有记录，无需修改即可使用
- 选择一条现有记录，将其与表单中的信息合并

以下是该函数的完整列表：

```
function write_customer(&$params)
{
    $dbh = db_connect();

    $output = TRUE;

    $action = 'insert';
    $duplicate = NULL;

    // set up default variables for all the fields in customers table
    // we end up with a key in params for every field in customers,
    // set to NULL if we have no value
    $customer_fields = $dbh->getCol('describe customers');
    foreach (array_diff($customer_fields, array_keys($params)) as $k)
        $params[$k] = NULL;

    // extract($params, EXTR_REFS);
    // workaround for "BOGUS" bug #24630 with extract() :
    // extracting with the EXTR_REFS flag will make any
    // variables used in *creating* the array into
    // references as well
    foreach (array_keys($params) as $k)
        $$k =& $params[$k];

    // the hours for day and evening phones are filled in by default.
    // if no phone number is given, set them to NULL

    if (empty($day_prefix)) { $day_start = NULL; $day_end = NULL; }
    if (empty($eve_prefix)) { $eve_start = NULL; $eve_end = NULL; }
```

