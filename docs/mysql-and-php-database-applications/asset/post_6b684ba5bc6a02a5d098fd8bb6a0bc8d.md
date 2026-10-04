
# 342 Part IV: Not So Simple Applications

```php
":
  $result = safe_query($query);
if (!$result) { die("no such problem: <pre>$query</pre>"); }
set_result_variables($result);
}
```

Here you are gathering all the information associated with a single problem_id.
For that, you need to join them on the sources status tables.

FIND_CUSTOM() Remember that you would like to enable users to report their problems over the Web. In this application, we've decided that there is a numeric primary key for each user, the application should be able to identify the user by a phone number or an e-mail. When a user enters information, you will need to check if someone with an identical e-mail or phone number has come along.

```php
function find_customer($email="",
  $day_area="",$day_prefix="",$day_suffix=""
  $eve_area="",$eve_prefix="",$eve_suffix="")
{
  $where = ""
  $sep = ""
  if ($day_prefix != "") {
    // there must be a prefix for this to be a valid phone number
    $where = '$day_area'
      and $day_prefix = '$day_prefix'
      and $day_suffix = '$day_suffix'
    $where .= $sep;
    // separate each part of the qualification with OR
    // any part constitutes a valid match.
    $sep = " or "
  }
  if ($eve_prefix != "") {
    // there must be a prefix for this to be a valid phone number
    //number
```

# Chapter 13: Problem Tracking System

```php
$where = "
  $sep
(eve_area = '$eve_area'
  and eve_prefix = '$eve_prefix'
  and eve_suffix = '$eve_suffix'
)

";
```

```php
$sep = " or ";
{
if ($email != "")
{
  $where = "
  $sep
  (email = '$email')
  ";
if ($where == "")
{
  // nothing to look for
  return FALSE;
}
}

```php
// run a query with the constructed qualification
// and return the result
$query = "select * from customers
where $where
order by customer_id
```

```php
";
$result = safe_query($query);
return $result;

```

With this function you will know if the user has an existing record that can be used or might need to be updated.

Notice the grouping of the portions of the where clause. It is looking for any one of three circumstances, each of which must meet a few criteria. For the e-mail, daytime phone and evening phone fields are filled in, this function will create a query that likes this:

```sql
select * from customers
where (day_area = '015'
  and day_prefix = '555'
  and day_suffix = '0410 ')
or (eve_area = '212'
  and eve_prefix = '555'
```

# 344 Part IV: Not So Simple Applications

and eve_suffix = '9999'
or (email = 'jay@trans-city.com')
order by customer_id

![](img/245156cc770929860a3ede93c01f9981_372_0.png)

If you were interested, you could set a cookie to make identifying the user bit easier.

PRESENT_DUPS() You need to plan for a couple of eventualities: if there are email addresses or phone numbers, but some other personal information has changed, you need to let the user update the database or discard the data. This function spots the redundancy and alerts the user.

```php
function present_dups($result)
{
  // we have to start the call entry form inside the function
  // use a global variable to indicate that this was done.
  $in_form = 1;

  // start the form
  print start_form("create_call.php");

  print paragraph("<b>
    We may have found you in our database.\n
    Please let us know what you would like to do:"\n
  </b>");

  print start_table();

  // for each customer record in the result set
  while ($row = mysql_fetch_array($result,MYSQL_ASSOC))
{
    // print out the ID value for the record in a radio field,
    // allowing the user to choose only one if more
    // one is displayed.
    print table_row(
```

# Chapter 13: Problem Tracking System

```php
radio_field(
  "customer_id",
  $row["customer_id"],
  "<b>Use this row</b>"
)
  "<b>Record #.$row["customer_id"]."</b>"
);
// print out the name & address information from this record
print table_row("",$row["firstname"].".$row["lastname"]);
if (!empty($row["address"]))
{
  print table_row("",$row["address"]);
}
if (!empty($row["address2"]))
{
  print table_row("",$row["address2"]);
}
if (!empty($row["city"]) || !empty($row["state"]))
|| !empty($row["zip"]))
{
  print table_row("",
    $row["city"].".$row["state"]." "
    $row["zip"]);
}
if (!empty($row["day_prefix"]))
{
  $daycell = "Day:"
  $row["day_area"]
  "."
  $row["day_prefix"]
  "."
  $row["day_suffix"]
}
if (!empty($row["day_ext"]))
{
  $daycell .= " - ".$row["day_ext"];
}
if (!empty($row["day_start"]))
```

# 346 Part IV: Not So Simple Applications

```php
$daycell .= " from ".$row["day_start"]];
}
if (!empty($row["day_end"]))
{
    $daycell .= " until ".$row["day_end"]];
    print table_row("",$daycell);
}
if (!empty($row["eve_prefix"]))
{
    $evecell = "Eve:"
        $row["eve_area"]
        "."
        $row["eve_prefix"]
        ."-"
        $row["eve_suffix"];
    if (!empty($row["eve_ext"]))
    {
        $evecell .= " ".$row["eve_ext"];
    }
    if (!empty($row["eve_start"]))
    {
        $evecell .= " from ".$row["eve_start"]];
    }
    if (!empty($row["eve_end"]))
    {
        $evecell .= " until ".$row["eve_end"]];
    }
    print table_row("",$evecell);
}
if (!empty($row["email"]))
{
    print table_row("",$row["email"]);
}
// print out a checkbox field allowing the user to
// indicate that this record should be overwritten
// with the information from the form.
print table_row("
    .checkbox_field("override")
```

# Chapter 13: Problem Tracking System

```php
$row["customer_id"]
"<b>Override this entry with the new</b>"
"<b>information in the form below.</b>"
```

```php
// print out a checkbox field allowing the user to
// indicate this record should be merged
// with the information from the form and the result
// written back to the database.
print table_row("
  checkbox_field(
    "merge",
    $row["customer_id"],
    "<b>Merge this entry with the new</b>"
    "<b>information in the form below.</b>"
  )
);
print end_table();
```

```php
// print out a final radio field indicating that, rather than
// using any of the records found in the database, a new record
// should be created.
print paragraph(radio_field(
  "add_as_new",
  "yes",
  "Create a new record with the information in the form
below."));
```

All the duplicate rows are printed, and the user can choose what to do with the data. You can see this in action if you go to the index.php page of this application and attempt to enter two different tickets with, say, the same phone number. Figure 13-6 gives an example.

# 348 Part IV: Not So Simple Applications

![](img/245156cc770929860a3ede93c01f9981_376_0.png)

Figure 13-6: For updating customer information

HISTORY_ENTRY When a staff member enters an update on a problem, the step is stored in the history table. If the entry is "public" user will be e-mailed with the update; if not, there will be no e-mail.
Notice the interesting query. The here inserts contain a statement. The only thing this select is actually getting the source_id related to the variable $source. All the rest of the insert information comes from variables.

```php
function history_entry
($problem_id="",$entry_type_id="",$entered_by="",
$source="",$notes="")
{
	if (empty($problem_id)) { return FALSE; }
	if (empty($entered_by)) { $entered_by = "customer"; }
	// create a record in the history table, getting the ID value
// of the source from the sources table.
	$query = "insert into history
(problem_id,entry_type_id,entered_by,source_id,notes)
	select '$problem_id',$entry_type_id,'entered_by',
```

# Chapter 13: Problem Tracking System

```php
source_id, '$notes'
from sources where source = '$source'
```

```php
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
and et.entry_type = h.entry_type_id
and et.entry_type = 'public'
and h.problem_id = p.problem_id
and p.customer_id = c.customer_id
and c.email != '' and c.email is not null");

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

# NOTIFY_CUSTOMER() This function constructs an e-mail and sends it.

```php
function notify_customer ($problem_id="", $email="", $notes="",
$problem_code="")
```
