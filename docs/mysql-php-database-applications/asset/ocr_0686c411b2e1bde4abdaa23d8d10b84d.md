```
, E_USER_NOTICE
 );
 return FALSE;
 }

 // run a query with the constructed qualification
 // and return the result.
 // separate each part of the qualification with OR -
 // any part constitutes a valid match.
 $query = 'select * from customers where '
 . 'implode(' or ', $wheres)
 . ' order by customer_id '
 ;

 $results = db_connect()->getAll($query, $bind,
 DB_FETCHMODE_ASSOC);
 return $results;
 }
```

With this function you will know if the user has an existing record that can be used or that might need to be updated. Figure 13-6 shows the form for updating customer data.

![](bbox=[0.16, 0.51, 0.82, 0.89])

Figure 13-6: Form for updating customer information