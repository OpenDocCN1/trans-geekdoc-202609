```
$query = 'select stage_id, stage, stage_table from stages
       where stage_id = ?
union
select stage_id, stage, stage_table from stages
       having stage_id = min(stage_id)
';
$row = db_connect()->getRow(
    $query
    , array($stage_id)
    , DB_FETCHMODE_ORDERED
);
if ($row)
{
    list($stage_id,$stage,$stage_table) = $row;
}
else
{
    user_error('Unable to get current stage for this story'
        . E_USER_ERROR
    );
}

// create or update a record for this story in the stage access
// table for the new stage.
$result = db_connect()->query(
    'replace into ! (story_id) values (?)'
    , array($stage_table,$story_id)
);
if (!$result)
{
    if (preg_match('/denied to user/', db_connect()->
>error_message()))
{
    error = "Access denied to $stage for $username";
}
else
{
    error = 'Database error - could not update stage';
}
    user_error($error, E_USER_ERROR);
}

if (!empty($publish_yr) && !empty($publish_mn) &&
!empty($publish_dy))
{
```