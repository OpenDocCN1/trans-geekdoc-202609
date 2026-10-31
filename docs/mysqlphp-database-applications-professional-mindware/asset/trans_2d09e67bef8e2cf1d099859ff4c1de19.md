
radio_field(
    "customer_id"
    , $row["customer_id"]
    , "<b>Use this row</b>"
)
, "<b>Record #". $row["customer_id"]. "</b>"
);

// 从该记录打印出姓名和地址信息
print table_row("",$row["firstname"]." ".$row["lastname"]);
if (!empty($row["address"]))
{
    print table_row("",$row["address"]);
}
if (!empty($row["address2"]))
{
    print table_row("",$row["address2"]);
}
if ( !empty($row["city"]) || !empty($row["state"])
    || !empty($row["zip"])
)
{
    print table_row("")
        , $row["city"].", ".$row["state"]." "
        .$row["zip"]
    );
}
if (!empty($row["day_prefix"]))
{
    $daycell = "Day: "
        .$row["day_area"]
        ." "
        .$row["day_prefix"]
        ." -"
        .$row["day_suffix"]
    ;
    if (!empty($row["day_ext"]))
    {
        $daycell .= " ".$row["day_ext"];
    }
    if (!empty($row["day_start"]))
    {
```php
$daycell .= " from ".$row["day_start"];
}
if (!empty($row["day_end"]))
{
    $daycell .= " until ".$row["day_end"];
}
print table_row("",$daycell);
}
if (!empty($row["eve_prefix"]))
{
    $evecell = "Eve: "
        .$row["eve_area"]
        ." "
        .$row["eve_prefix"]
        ."_"
        .$row["eve_suffix"]
    ;
    if (!empty($row["eve_ext"]))
    {
        $evecell .= " ".$row["eve_ext"];
    }
    if (!empty($row["eve_start"]))
    {
        $evecell .= " from ".$row["eve_start"];
    }
    if (!empty($row["eve_end"]))
    {
        $evecell .= " until ".$row["eve_end"];
    }
    print table_row("",$evecell);
}
if (!empty($row["email"]))
{
    print table_row("",$row["email"]);
}

// 打印出一个复选框字段，允许用户
// 指示应覆盖此记录
// 使用表单中的信息。
print table_row("")
    , checkbox_field(
        "override"
```
, $row["customer_id"]
, "<b>Override this entry with the new"
. " information in the form below.</b>"
)
);

// 打印出一个复选框字段，允许用户
// 指示应将此记录与表单中的信息合并
// 并将结果写回数据库。
print table_row(""
    , checkbox_field(
        "merge"
        , $row["customer_id"]
        , "<b>Merge this entry with the new"
        . " information in the form below.</b>"
    )
);
}
print end_table();

// 打印出一个最终的单选字段，指示与其使用数据库中找到的任何记录，不如创建一个新记录。
print paragraph(radio_field(
    "add_as_new"
    , "yes"
    , "Create a new record with the information in the form
below."
));

}

所有重复的行都会被打印出来，用户可以选择如何处理数据。你可以在本应用的 index.php 页面上看到此功能，如果尝试使用相同的电话号码输入两个不同的工单。图 13-6 给出了一个示例。

![](img/de0823012275cf4ceebdb822a56e6b71_376_0.png)

Figure 13-6: 用于更新客户信息的表单

## HISTORY_ENTRY()

当工作人员对问题进行更新时，该步骤会存储在历史表中。如果条目为“public”，用户将通过电子邮件收到更新；如果不是，则不会发送电子邮件。

请注意这个有趣的查询。这里的 insert 包含一个 select 语句。这个 select 实际获取的唯一内容是与变量 $source 相关的 source_id。其余所有插入信息都来自变量。

```
function history_entry
($problem_id="",$entry_type_id="",$entered_by=""
,$source="",$notes=""
)
{
    if (empty($problem_id)) { return FALSE; }
    
    if (empty($entered_by)) { $entered_by = "customer"; }
    
    // create a record in the history table, getting the ID value
    // of the source from the sources table.
    $query = "insert into history
(problem_id,entry_type_id,entered_by,source_id,notes)
        select '$problem_id',$entry_type_id,'$entered_by',
```
source_id, '$notes'
        from sources where source = '$source'
";
$result = safe_query($query);
if ($result)
{
    // get the ID value of the new history record
    // (automatically assigned by MySQL).
    $entry_id = mysql_insert_id();

    // get the email address of
    // the customer who opened this call
    // if this was a public history
    // entry, and if the email address
    // is not empty
    $cresult = safe_query("select c.email
        from problems p, customers c, history h, entry_types et
        where h.entry_id = $entry_id
        and et.entry_type_id = h.entry_type_id
        and et.entry_type = 'public'
        and h.problem_id = p.problem_id
        and p.customer_id = c.customer_id
        and c.email != '' and c.email is not null
");
    if ($cresult && mysql_num_rows($cresult))
    {
        // we have a valid email address - use it to
        // notify the customer that the call record
        // has been updated.
        list($email) = mysql_fetch_array($cresult);
        notify_customer($problem_id,$email,$notes);
    }
}

    // return the result of the creation of the new history record
    return $result;
}
```

如果更新是公开的，则会运行 notify_customer() 函数。

## NOTIFY_CUSTOMER()
此函数构建电子邮件并发送它。

```
function notify_customer ($problem_id="", $email="", $notes="",
$problem_code="")
{
```
```php
// the Apache global variable $SERVER_NAME is the name
// of the server we're running on, minus any port number.
global $SERVER_NAME;

// remove any HTML tags and backslashes from $notes.
$notes = stripslashes(cleanup_text($notes));

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
        safe_query("update problems
            set problem_code = '$problem_code'
            where problem_id = $problem_id
        ");
    }
    // build an absolute URL calling the problem_status.php page
    // to check on this problem
    $problem_url =
regular_url("problem_status.php?problem_code=$problem_code");

// set the body of the email
$msgtext = <<<EOO

Problem Update:

$notes

You can check the current status of this problem at

$problem_url
Thanks for your patience.

EOO;

// set the headers of the email
$headers = "From: webmaster@".$SERVER_NAME."\n"
    ."Reply-To: webmaster@".$SERVER_NAME."\n"
    ."X-Mailer: PHP/".phpversion()
```
; 

// send the email
return mail($email, "Problem Update", $msgtext, $headers);
}
```

![](img/de0823012275cf4ceebdb822a56e6b71_379_0.png)

PHP 必须能够找到 sendmail 或其他 SMTP 兼容的邮件服务器才能使其工作。如果遇到问题，请检查你的 php.ini 文件。

## STATUS_CHANGE()

问题的状态将类似于“open”、“closed”或“pending”。如果它发生变化，你将希望标记确切的更改并记录类似“status changed to closed by John”的内容。更改应记录在历史表中。

```
function status_change($problem_id=""
    ,$new_status_id=""
    ,$old_status_id=""
    , $entered_by="customer"
)
{
    if (empty($problem_id) || empty($new_status_id)
        || $old_status_id == $new_status_id
    )
    {
        return;
    }

    if (empty($entered_by)) { $entered_by = "customer"; }

    // get the ID of the entry_type 'public', and construct
    // a string containing the new status value and either
    // the real name of the staff member who made the change,
    // or the value of $entered_by if no matching staff
    // member is found. for example, if the staff member Joe Blow
    // closes a call, the notes field will be set to
    // "Status set to Closed by Joe Blow". if a customer
    // re-opens a call, notes will be set to
    // "Status set to Re-opened by customer".

    // all of this depends on the value in $new_status_id
    // being a valid ID of a record in the status table.
    $query = "select et.entry_type_id
```
