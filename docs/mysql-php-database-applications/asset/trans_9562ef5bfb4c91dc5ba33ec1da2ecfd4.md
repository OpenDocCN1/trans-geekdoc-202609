

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

该函数与 fetch_story() 的工作方式类似，但允许我们为 modify_dt 值指定一个值。

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

该函数与 fetch_story() 函数的工作方式类似，但它是对作者表进行操作，以查找指定作者的所有故事。

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

该函数也以类似于 fetch_story 函数的方式工作，但它是查找给定用户的帖子。

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

stage() 和 stage_id() 函数是主 stages() 函数的前端。第一次调用 stages() 时，数据库中 stages 表的内容会被加载到静态数组中。这样，我们就可以在后续调用中通过 ID 值查找阶段名称，反之亦然，而无需查询数据库。

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

我们为故事经历的工作流中的每个阶段构建单独的表。会分配 MySQL 权限，允许应用程序的单个用户访问这些表。此函数将阶段名称转换为相应的阶段表名。

```
function stage_table_name($stage)
{
	return preg_replace('/ /', '-',
	    strtolower(trim($stage)).'_stories');
}
```

## write_author()

write_author() 函数在数据库的作者表中创建或更新记录。

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

write_story() 函数在数据库的故事表中创建或更新记录。它还会将故事从一个阶段移动到另一个阶段。由于用户可能尝试修改其无权访问的阶段中的故事，或在工作流中将故事向前或向后发送到受限阶段，因此查询可能会导致 MySQL 权限错误。我们不希望应用程序在这种情况下仅回滚事务并停止，因此我们使用 DB 类的 pushErrorHandling() 和 popErrorHandling() 方法（实际上，这些是从通用 PEAR Error 类继承的方法）来临时更改数据库错误的处理方式。

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

