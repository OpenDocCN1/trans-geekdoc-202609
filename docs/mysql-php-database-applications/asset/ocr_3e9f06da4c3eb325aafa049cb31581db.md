```
// the form.

$customer_code = $record['customer_code'];
$action = 'update';
}
else
{
    // use the customer's record from the database
    extract($record);
    $action = 'none';
}
}
```

```
elseif ($dup_action == 'add_as_new')
{
    // the user has clicked on a radio field indicating that
    // a new customer record should be created.

    // set $action to indicate that we should create a new record.
    // with the information from the form.
    $action = 'insert';
}
```

```
else
{
    // either we haven't checked for duplicate customer records yet,
    // or the user didn't tell us what to do about them.

    // use the find_customer() function (defined in functions.php)
    // to look for any existing customer records which might
    // match the customer described in the form.
    $result = find_customer($email
        , $day_area, $day_prefix, $day_suffix
        , $eve_area, $eve_prefix, $eve_suffix
    );
    if (count($result) == 0)
    {
        // either we don't have any contact information,
        // or no record was found matching this one.
        // set $action to indicate that we should go ahead
        // and create a new record.
        $action = 'insert';
    }
    else
    {
        $action = 'problems';
```