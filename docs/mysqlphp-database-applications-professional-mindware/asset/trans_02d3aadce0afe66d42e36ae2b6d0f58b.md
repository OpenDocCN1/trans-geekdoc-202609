
```
, concat('Status set to '
    , ns.status
    , ' by '
    , ifnull(t.staff_name,'$entered_by')
) as notes
    from entry_types et, status ns
left join staff t on t.username = '$entered_by'
where et.entry_type = 'public'
and ns.status_id = $new_status_id
";
$result = safe_query($query);
if ($result)
{
    // $new_status_id is a valid status ID - use the
    // history_entry() to make an entry in the history table
    // recording the status change, and send email notifying
    // the user.
    list($entry_type_id, $notes) = mysql_fetch_array($result);
    history_entry($problem_id, $entry_type_id, $entered_by
        , 'program', $notes
    );
}
}
```

## DISPLAY_CALL_LIST()
这是另一个便捷函数。它打印查询结果以及表头行。

```
function display_call_list($query="",$subtitle="Call List"
    , $script="edit_problem.php"
)
{
    if ($query == "") { return; }
    $result = safe_query($query);
    if (!$result) { return; }

    $calls = 0;
    while ($row = mysql_fetch_array($result))
    {
        if ($calls == 0)
        {
            // we want to print out the table header only once,
            // and only if there is at least one row -
            // do it when processing the first row
            // of the result set.
```

```
print subtitle($subtitle);

print start_table();

print table_row(
    "<b>Problem #</b>"
    , "<b>Date</b>"
    , "<b>Customer</b>"
    , "<b>Problem</b>"
    , "<b>Source</b>"
    , "<b>Status</b>"
);
}
$calls++;

// print out information about the call, including
// a link to the given script for updating its
// status and history.
print table_row($row["problem_id"]
    , $row["entry_dt"]
    , anchor_tag($script."?problem_id="
        .$row["problem_id"]
    , $row["firstname"]." ".$row["lastname"]
    )
    , $row["summary"]
    , $row["source"]
    , $row["status"]
);
}
if ($calls > 0)
{
    // there was at least one call, so the table was opened
    // close it.
    print end_table();
}
}
```

## CREATE_PROBLEM_CODE()
该函数创建一个唯一且高度随机的 8 位字母数字代码。

```
function create_problem_code()
{
    return substr(md5(uniqid(rand())),0,8);
}
```

## Scripts
以下是实际由 URL 和包含文件调用的页面。

### CALL_ENTRY.PHP
此页面几乎没有做什么，只是调用稍后讨论的 call_entry_form.php。

请记住，此表单可能由已登录的员工访问。请注意，员工应从 staff.php 页面开始登录。或者，您也可以使用 cookie 来确定员工身份。

如果识别出员工或用户，则所有与用户相关的信息都会通过适当的 fetch 函数设置为全局变量。

```
include "header.php";

if ($use_staff_name == "yes")
{
    db_authenticate("staff", "Bricks and Mortar Support");
    fetch_staff($PHP_AUTH_USER);
}

$page_title = $default_page_title.": Call Entry";
include "start_page.php";

if (!empty($customer_id))
{
    // a customer ID value was submitted - get the customer's
    // contact information from the database.
    fetch_customer($customer_id);
}

// call the script that actually displays the call entry form.
include "call_entry_form.php";

include "end_page.php";
```

### CALL_ENTRY_FORM.PHP
此表单主要调用 /book/functions/ 文件夹中的函数。它打印图 13-1 所示的表单并确定表单中的默认信息。call_entry.php 页面将包含此页面。

表单将提交到稍后讨论的 create_call.php 页面。

```
if (!$in_form)
{
    // if the user has submitted the form once and existing
    // contact information was found for the customer,
    // the present_dups() function (defined in functions.php)
    // will have already started the form, in order to
    // display the contact records to the user. in this case,
    // the function will set the global variable $in_form to 1.
    // if $in_form is not set, begin the form here.
    print start_form("create_call.php");
}

print start_table();

// print out the customer's contact information.
print table_row(table_cell("<b>Customer
Information</b>",array("colspan"=>2)));

print_row("First Name", text_field("firstname","$firstname",40));
print_row("Last Name", text_field("lastname","$lastname",40));
print_row("Email Address", text_field("email","$email",40));
print_row("Street Address", text_field("address","$address",40));
print_row("", text_field("address2","$address2",40, 40));
print_row("City", text_field("city","$city",40, 40));
print_row("State/Zip", text_field("state","$state",2, 2)
."&nbsp;"
.text_field("zip", "$zip", 5, 5)
."-"
.text_field("zip4", "$zip4", 4, 4)
);

// by default, daytime phone numbers cover the hours of 9 AM to 5
// PM.
if (empty($day_start)) { $day_start = "9:00 AM"; }
if (empty($day_end)) { $day_end = "5:00 PM"; }

print_row("Daytime Phone", "("
.text_field("day_area","$day_area",3,3)
.") "
.text_field("day_prefix","$day_prefix",3,3)
.text_field("day_suffix","$day_suffix",4,4)
."&nbsp;"
."<b>Ext:</b>\n"
.text_field("day_ext","$day_ext",5,5)
."&nbsp;"
."<b>Hours:</b>\n"
.text_field("day_start","$day_start",8,8)
```

```
.text_field("day_end","$day_end",8,8)
);

// by default, evening phone numbers cover the hours of 5 PM to 8
// PM.
if (empty($eve_start)) { $eve_start = "5:00 PM"; }
if (empty($eve_end)) { $eve_end = "8:00 PM"; }

print_row("Evening Phone", "("
    .text_field("eve_area","$eve_area",3,3)
    .") "
    .text_field("eve_prefix","$eve_prefix",3,3)
    .text_field("eve_suffix","$eve_suffix",4,4)
    ."&nbsp;"
    ."<b>Ext:</b>\n"
    .text_field("eve_ext","$eve_ext",5,5)
    ."&nbsp;"
    ."<b>Hours:</b>\n"
    .text_field("eve_start","5:00 PM",8,8)
    .text_field("eve_end","8:00 PM",8,8)
);

// spacer row to separate the two main areas of the form - we have
// to use a blank space (&nbsp;) to fill out the table cell, or it
// won't show up (much).
print table_row(table_cell("&nbsp;",array("colspan"=>2)));

// print out fields for describing the problem.
print table_row(table_cell("<b>Problem
Description</b>",array("colspan"=>2)));

if (!empty($use_staff_name))
{
    // if a staff member is entering a problem record, record
    // the fact in hidden fields.
    print_row("Entered by", $username
        .hidden_field("entered_by", $username)
        .hidden_field("use_staff_name", $use_staff_name)
    );

    // allow the staff member to indicate the original source of the
    // problem report.
    print_row("Source"
        , db_select_field("source_id", "sources", "source_id",
"source")
```

```
);
}

print_row("Brief summary of problem"
, textarea_field("summary",$summary, 40, 2)
);

print_row("Complete Problem Description"
, textarea_field("problem",$problem, 40, 15)
);

print end_table();

print paragraph(
    submit_field("submit","Submit Problem Report")
, reset_field()
);

print end_form();
```

### CREATE_CALL.PHP
此页面很长，但并不太复杂。我会在遇到有趣的部分时进行讨论。当您查看它时，最容易了解它可以完成的操作种类。以下是该页面的逻辑概述：

```
customer or staff comes to call_entry
    if customer_id is available
        fetch that record
        display it in the form
    else
        display blank form

    if email or phone number have no match in db
        create new customer address
    else
        if more than one records match
            present records to customer
            allow customer to:
                - create new record with new info
                - use an existing record
                - override an existing record with new info
                - merge new info with an existing record;
                  where existing has values and new
                  does not, existing will be used
                - mark one of the records as a duplicate
                  to be purged; calls tied to it
                  will be linked to the record
                  used for this call
            present new info in form to allow for updating
        else
          if no new info overrides existing record
            use existing record
          else
            present record to customer
          allow customer to:
            - create new record with new info
            - use existing record
            - override existing record with new info
            - merge new info with existing record;
              where existing has values and new
              does not, existing will be used
        present new info in form to allow for updating
```

有了这个概述，您应该能够在没有太大困难的情况下阅读该页面的源代码，当然它在 CD-ROM 上。

### STAFF.PHP
这是您期望员工登录应用程序的地方。请注意 staff_authenticate() 函数的使用，它调用了您在整本书中一直使用的 authenticate() 函数。在员工能够登录之前，他或她必须输入有效的密码和用户名。

该页面将显示两个查询列表，一个是当前登录员工拥有的呼叫列表，另一个是未拥有的呼叫列表，可能是在 Web 上输入的内容。

```
include "header.php";
staff_authenticate();

fetch_staff($PHP_AUTH_USER);

$page_title = $default_page_title." : $PHP_AUTH_USER";
include "start_page.php";

// first, get a list of all open unowned calls and display them,
// in the hopes that the user might grab one.
$query = "select c.customer_id, c.firstname, c.lastname
    , p.problem_id
```
