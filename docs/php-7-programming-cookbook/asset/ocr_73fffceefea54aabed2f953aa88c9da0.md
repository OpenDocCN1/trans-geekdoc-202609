Note that addField() returns the current mapping instance so there is no need to keep specifying $mapper->addField(). This technique is referred to as the fluent interface.

The name field is tricky, as in the prospects_11 table it's represented by two columns, but only one column in the customer_11 table. Accordingly, you can add a callback as default for first_name to combine the two fields into one. You will also need to define an entry for last_name but where there is no destination mapping:

```
`->addField(new FieldConfig('first_name','customer_11','name', function ($row) { return trim($row['first_name'] ?? '') . ' ' . ($row['last_name'] ?? '');}) ->addField(new FieldConfig('last_name'))`
```

The customer_11::status field can use the null coalesce operator (??) to determine if it's set or not:

```
`->addField(new FieldConfig('status','customer_11','status', function ($row) { return $row['status'] ?? 'Unknown';}))`
```

The customer_11::level field is not represented in the source table, thus you can make a NULL entry for the source field, but make sure the destination table and column are set. Likewise, customer_11::password is not present in the source table. In this case, the callback uses the phone number as a temporary password:

```
`->addField(new FieldConfig(NULL,'customer_11','level','BEG')) ->addField(new FieldConfig(NULL,'customer_11','password', function ($row) { return $row['phone'];})`
```

You can also set mappings from prospects_11 to profile_11 as follows. Note that as the source photo and date of birth columns are not present in prospects_11, you can set any appropriate default:

```
`->addField(new FieldConfig('address','profile_11','address')) ->addField(new FieldConfig('city','profile_11','city')) ->addField(new FieldConfig('state_province','profile_11', 'state_province', function ($row) { return $row['state_province'] ?? 'Unknown'; })) ->addField(new FieldConfig('postal_code','profile_11', 'postal_code')) ->addField(new FieldConfig('phone','profile_11','phone')) ->addField(new FieldConfig('country','profile_11','country')) ->addField(new FieldConfig(NULL,'profile_11','photo', DEFAULT_PHOTO)) ->addField(new FieldConfig(NULL,'profile_11','dob', date('Y-m-d')));`
```