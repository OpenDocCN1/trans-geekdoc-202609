```
// insert the new record into the topics table
$query = sprintf(
    "insert into topics
    (name,description, parent_id, root_id, author,
    author_addr_id)
    values ('%s','%s',%d,%d,'%s','%s')"
    , mysql_real_escape_string($name)
    , mysql_real_escape_string($description)
    , $p['parent_id']
    , $p['root_id']
    , mysql_real_escape_string($author)
    , $author_addr_id
);

// begin transaction
my_query('begin');

my_query($query);

$topic_id = mysql_insert_id();
if ($p['root_id'] == 0)
{
    // if the root_id is zero, that means that this
    // topic is itself a root topic.  set the root_id
    // column of its database record to that ID value
    // (a root topic is its own root)
    my_query(
    'update topics set root_id = topic_id where root_id = 0'
    );
}

// end transaction
my_query('commit');

return $topic_id;
}
```

This function simply inserts the data into the database. All the information is coming from an HTML form.

In going through these functions, you might notice that you never check to see if the result of a query is false. You can get away with this because you aren't getting away with it, really; you're just checking in the reusable my_query() function.