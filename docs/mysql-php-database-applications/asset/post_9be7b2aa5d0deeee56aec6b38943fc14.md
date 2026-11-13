
else
{
    $this_username = NULL;
}
if (is_assoc($args))
{
    extract($args, EXTR_IF_EXISTS);
}
elseif (is_numeric($args))
{
    $story_id = $args;
}

```
$query = <<<EOQ
select m.user_id as is_ok
    , s.*
    , date_format(s.publish_dt, '%Y') as publish_yr
    , date_format(s.publish_dt, '%m') as publish_mn
    , date_format(s.publish_dt, '%d') as publish_dy
    , t.stage, t.stage_table
from stories s
    left join stages t on s.stage_id = t.stage_id
    left join users u on u.username = ifnull(?, user())
    left join user_stage_map m on s.stage_id = m.stage_id
    and m.user_id = u.user_id
EOQ;
```

```
$bind = array($this_username);
if ($story_id)
{
    $query .= ' where s.story_id = ? ';
    $bind[] = $story_id;
}
```

```
$result = db_connect()->getRow($query, $bind,
    DB_FETCHMODE_ASSOC);
    return $result;
}
```

## fetch_story_version()

This function works like fetch_story(), except that it allows us to specify a value for the modify_dt value.

```
<?php
function fetch_story_version ($args=NULL)
{
    $story_id = NULL;
    $modify_dt = NULL;
    $this_username = $_SESSION['PHP_AUTH_USER'];
    if (is_assoc($args))
    {
        extract($args, EXTR_IF_EXISTS);
    }
    elseif (is_array($args))
    {
        $story_id = array_shift($args);
        $modify_dt = array_shift($args);
        $this_username = array_shift($args);
    }
    elseif ($args !== NULL)
    {
        $story_id = $args;
    }

    $query = <<<EOQ
    select m.user_id as is_ok
        , s.*
        , date_format(s.publish_dt, '%Y') as publish_yr
        , date_format(s.publish_dt, '%m') as publish_mn
        , date_format(s.publish_dt, '%d') as publish_dy
        , t.stage, t.stage_table
    from story_versions s
        left join stages t on s.stage_id = t.stage_id
        left join users u on u.username = ifnull(?, user())
        left join user_stage_map m on s.stage_id = m.stage_id
        and m.user_id = u.user_id
    EOQ;

    $bind = array($this_username);
    $wheres = array();
    if ($story_id)
    {
        $wheres[] = 's.story_id = ?';
        $bind[] = $story_id;
    }
    if ($modify_dt)
    {
        $wheres[] = 's.modify_dt = ?';
        $bind[] = $modify_dt;
    }
}
if (count($wheres) > 0)
{
    $query .= ' where '.implode(' and ', $wheres);
}

$result = db_connect()->getRow($query, $bind,
DB_FETCHMODE_ASSOC);
return $result;
}
?>
```

## function fetch_author()

This function works similarly to the fetch_story() function, except that it operates on the authors table to find all the stories by a specified author.

```
function fetch_author ($args=array())
{
    $author_id = NULL;
    $other = NULL;
    if (is_assoc($args))
    {
        extract($args, EXTR_IF_EXISTS);
    }
    else
    {
        $author_id = $args;
    }
    $args = array('table'=>'authors');
    if ($author_id)
    {
        $args['key'] = 'author_id';
        $args['value'] = $author_id;
    }
    if (is_assoc($other))
    {
        $args = array_merge($args, $other);
    }
    return db_fetch_record($args);
}
```

## fetch_user()

This function also works similarly to the fetch_story function, except it looks for postings by a given user.

```
function fetch_user ()
{
	$params = array('table'=>'users');
	$args = func_get_args();
	foreach ($args as $arg)
	{
		if (is_assoc($arg))
		{
			$params = array_merge($params, $arg);
		}
		elseif (is_numeric($arg))
		{
			$params['key'][] = 'user_id';
			$params['value'][] = $arg;
		}
		elseif (is_string($arg))
		{
			$params['key'][] = 'username';
			$params['value'][] = $arg;
		}
	}
	return db_fetch_record($params);
}
```

## stage(), stage_id(), stages()

The stage() and stage_id() functions are front ends to the main stages() function. The first time stages() is called, the contents of the stages table from the database are loaded into a static array. This enables us to make subsequent calls to look up a stage name by its ID value, or vice versa, without querying the database.

```
<?php
function stage($stage_id=NULL)
{
	return stages('stage_id',$stage_id);
}
function stage_id($stage=NULL)
{
	return stages('stage',$stage);
}
function stage_table($stage_id=NULL)
{
	return stages('stage_table',$stage_id);
}
function stages($key=NULL,$value=NULL)
{
	static $stages = NULL;
	if ($stages == NULL)
	{
	 $result = db_connect()->query(
	 'select * from stages order by stage_id'
	 );
	 while ($row = $result->fetchRow(DB_FETCHMODE_ASSOC))
	 {
	 extract($row);
	 $stages['stage'][$stage] = $stage_id;
	 $stages['stage'][''][''] = $stage_id;
	 $stages['stage_id'][$stage_id] = $stage;
	 $stages['stage_id'][''][''] = $stage;
	 $stages['stage_table'][$stage_id] = $stage_table;
	 $stages[''][''] = $row;
	 }
	 $result->free();
	}
	if (empty($key))
	{
	 return $stages[''][''];
	}
	elseif (array_key_exists($key,$stages))
	{
	 if (empty($value))
	 {
	 return $stages[$key][''][''];
	 }
	 elseif (array_key_exists($value,$stages[$key]))
	 {
	 return $stages[$key][$value];
	 }
	}
	return NULL;
}
?>
```

## stage_table_name()

We build a separate table for each stage of the workflow through which a story passes. MySQL permissions are assigned, allowing individual users of the application to access these tables. This function converts a stage name into the name of the corresponding stage table.

```
function stage_table_name($stage)
{
	return preg_replace('/ /', '-',
	    strtolower(trim($stage)).'_stories');
}
```

## write_author()

The write_author() function creates or updates a record in the authors table in the database.

```
function write_author($args=array())
{
    $author_id = NULL;
    $author = NULL;
    $email = NULL;
    $bio = NULL;
    if (is_assoc($args))
    {
        extract($args, EXTR_IF_EXISTS);
    }
    else
    {
        $private_error = 'bad arguments to write_author:'
            . var_export($args, TRUE)
        ;
        user_error(
            'Invalid arguments - could not write author'
            . E_USER_WARNING
        );
        return FALSE;
    }

    if (empty($author_id))
    {
        // if we don't have an ID value, no record exists
        // for this author - create one.
        $author_id = db_connect()->nextId('author');
        $stmt = db_connect()->prepare(
            'insert into authors (author,email,bio,author_id) values
            (?,?,?,?)'
        );
    }
    else
    {
        // if we have an ID value, a record currently exists
        // for this author - update it.
        $stmt = db_connect()->prepare(
            'update authors set author=?, email=?, bio=? where
            author_id = ?'
        );

        $result = db_connect()->execute($stmt,
            array($author,$email,$bio,$author_id));
        if (!$result)
        {
            user_error('Could not update author record',
                E_USER_WARNING);
            return FALSE;
        }
        return TRUE;
    }
}
```

## write_story()

The write_story() function creates or updates a record in the stories table in the database. It also moves a story from one stage to another. Because a user may attempt to modify a story that is in a stage to which the user does not have access, or send a story forward or backward in the workflow to a restricted stage, we may end up getting MySQL permission errors from a query. We don't want the application to simply roll back the transaction and stop when this happens, so we use the DB class pushErrorHandling() and popErrorHandling() methods (actually, these are methods inherited from the general PEAR Error class) to temporarily change the way database errors are handled.

```
<?php
function start_dbhandler()
{
    db_connect()->pushErrorHandling(PEAR_ERROR_TRIGGER,
        E_USER_NOTICE);
}
function end_dbhandler($result=TRUE)
{
    db_connect()->popErrorHandling();
    return $result;
}

function write_story($args=array())
{
    $stage_id = NULL;
    $publish_yr = NULL;
    $publish_mn = NULL;
    $publish_dy = NULL;
    $publish_dt = NULL;
    $headline = NULL;
    $subtitle = NULL;
    $byline_prefix = NULL;
    $summary = NULL;
    $body = NULL;
    $story_id = 'NULL';
    $submit = NULL;
    $author = NULL;
    $author_id = NULL;

    if (is_assoc($args))
    {
        extract($args, EXTR_IF_EXISTS);
    }
    else
    {
        $private_error = 'write_story: error: bad arguments: '
            . var_export($args, TRUE)
        ;
        user_error('Could not update story', E_USER_WARNING);
        return FALSE;
    }

    start_dbhandler();

    // begin transaction
    db_connect()->query('begin');

    if (empty($story_id))
    {
        // if we have no ID value, this is a new story.
        // get the ID value of a new record from story sequence
        $story_id = db_connect()->nextId('story');
        $result = db_connect()->query(
            'insert into stories (story_id,headline) values (?,?)',
            array($story_id,'Not Yet Updated')
        );
        if (!$result)
        {
            db_connect()->query('rollback');
            user_error(
                'Could not insert new record into stories table'
            );
        }
    }
}
