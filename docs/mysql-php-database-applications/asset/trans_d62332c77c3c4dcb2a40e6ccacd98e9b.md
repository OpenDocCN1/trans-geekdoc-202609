
, description
    , author_addr_id
from topics
where parent_id = $topic_id
order by create_dt, topic_id"
;
$result = my_query($query);
$output = '';
while ($r = mysql_fetch_assoc($result))
{
    extract($r, EXTR_PREFIX_ALL, 'r');

    if (empty($r_author))
    {
        $r_author = '[no name]';
    }

    if ($r_topic_id != $topic_id)
    {
        $tag = anchor_tag(
            'index.php?topic_id=' . $r_topic_id
            , $r_name
        );
    }
    else
    {
        // this should never happen, but just in case -
        // don't print a link back to this topic
        $tag = $r_name;
    }

    $tag .= " by <b>$r_author</b> (ID#$r_author_addr_id) on
<b>$r_create_dt</b>";

    if ($level)
    {
        // non-zero level - use unordered list format
        $output .= li_tag($tag);
    }
    else
    {
        // zero (first) level - print inside a table
        $output .= table(array(
            'width' => '75%',
            'rows'=>array(
                table_row(table_cell(array(
                    'bgcolor'=>'skyblue'
                    , 'colspan'=>2
                    , 'value'=>$tag
                )))
            )
            , table_row(
                table_cell(array(
                    'width'=>5
                    , 'value'=>'&nbsp;&nbsp;'
                ))
            )
            , $r_description
        )
    ));
}
// display any child topics of this child, at the next
// higher level
$output .= display_kids($r_topic_id, $level+1);
}
mysql_free_result($result);

if ($output)
{
    if ($level)
    {
        // if not the first level and at least one child
        // was found,
        // display it as an unordered list
        $output = ul_list(array('contents'=>$output));
    }
    else
    {
        // this is the first child record:
        // - print out a header
        $output = "<b>Comments:</b><br>\n$output";
    }
}
return $output;
}

## display_topic()

该函数显示给定主题的信息。如果未指定 topic_id，则显示根级主题列表。

function display_topic ($topic_id=0, $show_kids=1, $level=0)
{
	$topic_id = (int)$topic_id;
	$show_kids = (int)$show_kids;
	$level = (int)$level;
}

如果未指定 topic_id，则执行以下部分。它显示根级主题。

if (!$topic_id)
{
	// no topic_id given - get all root topics
	$query = 'select topic_id, name from topics where topic_id = root_id';
	$result = my_query($query);
}

前面的代码片段中的查询会获取所有根级主题。紧随其后的 while... 循环会将每个主题作为 HTML 锚点打印出来，例如 <a href="index.php?topic_id=1">Topic name</a>。完成后，它会从函数中返回。

while (list($r_topic_id,$r_name) = mysql_fetch_row($result))
{
	// print the name of each topic as
	// a link to this script, passing in
	// the topic_id
	print paragraph(anchor_tag(
		'index.php?topic_id='. $r_topic_id
		. $r_name
		));
	}
	mysql_free_result($result);
	return;
}

如果 topic_id 可用，则以下查询会获取指定 topic_id 的父主题和根主题。外部连接确保查询会返回当前主题的信息，即使父主题或根主题已丢失。

$query = "select distinct current.parent_id
	. current.root_id
	. current.name
	. current.description
, current.author
, date_format(current.create_dt,'%b %e %Y %r') as
create_dt
, date_format(current.modify_dt,'%b %e %Y %r') as
modify_dt
, current.author_addr_id
, parent.name as parent_name
, root.name as root_name
from topics current
left join topics as parent
on current.parent_id = parent.topic_id
left join topics as root
on current.root_id = root.topic_id
where current.topic_id = $topic_id "
;
$result = my_query($query);
$r = mysql_fetch_assoc($result);
mysql_free_result($result);
if ($r == FALSE)
{
    print paragraph('<b>Error:</b> No such topic.');
    return;
}
extract($r);

if (empty($author)) { $author = '[no name]'; }

if ($root_id != $topic_id && $root_id != $parent_id)
{
    // if the root topic is something other than the current
    // topic or its immediate parent, print out its name
    // as a link to it
    if ($root_name == '') { $root_name = '[no topic name]'; }
    print paragraph(
        '<b>root:</b>'
        , anchor_tag('index.php?topic_id='.$root_id
        , $root_name
        )
    );
}

如果存在父主题，则会打印主题名称及其链接。

if (!empty($parent_name))
{
    // if an immediate parent was found, print out its name
    // as a link to it
    print paragraph(
        '<b>parent:</b>'
        , anchor_tag('index.php?topic_id=' . $parent_id
        , $parent_name
        )
    );
}
// print out the current topic
print paragraph(
    "<b>$name</b> by <b>$author</b> (ID#$author_addr_id) on
<b>$create_dt</b>"
);
print paragraph($description);
if ($show_kids)
{
    // print out a link to where the user to reply to
    // the current topic
    print paragraph(
        anchor_tag('write_topic.php?topic_id=' . $topic_id
        . '<b>Reply to this</b>')
    );
    // now display any children of the current topic
    print paragraph(display_kids($topic_id, $level));
}
// return information retrieved about the current topic
return array('root_id'=> $root_id, 'parent_id'=> $parent_id,
'name'=> $name);
}

## create_topic()

该函数将表单中获取的数据插入数据库。如前所述，我们从 $_SERVER['REMOTE_ADDR'] 变量中获取 IP 地址，并用其生成一个唯一 ID 号，该 ID 号也会被插入数据库。

许多字段（例如 $root_id）来自隐藏表单字段。如果用户试图创建新的顶级主题，则 root_id 设置为 0。在这种情况下，parent_id 需要设置为与 topic_id 相同的值。

function create_topic()
{
    static $defaults = array(
        'name' => 'no name'
        , 'description' => '[no comments]'
        , 'parent_id' => 0
        , 'root_id' => 0
        , 'author' => '[no author]'
    );

    static $simple = array();
    $args = func_get_args();
    $p = parse_arguments($args, $simple, $defaults);

    // run the topic name, description, and author through the
    // cleanup_text() function (defined in /book/functions/base.php)
    // to remove HTML tags and other special characters.

    $name = cleanup_text($p['name']);
    $description = cleanup_text($p['description']);
    $author = cleanup_text($p['author']);

    // we want to know that the same person is having a conversation
    // with himself, but these days storing real IP addresses is a
    // bit hinky. this serves our purpose just as well.
    $author_addr =
    array_key_value($_SERVER,'REMOTE_ADDR','unknown');
    $_addr = crypt($author_addr,$author_addr);
    $result = my_query("select author_addr_id from author_addrs
        where author_addr = '$author_addr'"
    );
    if (mysql_num_rows($result))
    {
        list($author_addr_id) = mysql_fetch_row($result);
    }
    else
    {
        my_query(
            "insert into author_addrs (author_addr) values
            ('$author_addr')"
        );
        $author_addr_id = mysql_insert_id();
    }
    mysql_free_result($result);
}

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

该函数只是将数据插入数据库。所有信息都来自 HTML 表单。

在浏览这些函数时，你可能会注意到你从未检查查询结果是否为 false。你之所以可以这样做，并非真的可以这样做；你只是在可复用的 my_query() 函数中进行检查。
