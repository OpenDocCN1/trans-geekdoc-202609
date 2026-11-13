
关于 DB::nextId() 方法的注意事项：如果在调用此方法时包含 ID 值的表不存在，该方法将尝试创建它。由于 Web 应用程序的用户账户通常没有创建表的权限，这很可能导致运行时错误。你应确保事先已创建这些表。表名为 sequencename_seq，其中 sequencename 是你传入 DB::nextId() 的名称。

```
if (empty($user_id))
{
    // if we don't have an ID value, there is no record
    // for this user - create one
    $user_id = db_connect()->nextId('user');
    $query = 'insert into users
    (username, password, name, email, user_id)
    values (?, password(?), ?, ?, ?) '
    ;
}
else
{
    // if we have an ID value, a record for this user
    // currently exists in the users table - update it
    $query = 'update users set username=?
    , password=password(?), name=?
    , email=?
    where user_id = ?'
    ;
}

$stmt = db_connect()->prepare($query);
$bind = array($username,$password,$name,$email,$user_id);
if (!db_connect()->execute($stmt,$bind))
{
    $private_error = db_connect()->last_query;
    user_error('could not update user record', E_USER_WARNING);
    return FALSE;
}
```

注意：当脚本的这一部分完成后，user_id 已知：
要么它是从表单传递来的，要么是通过调用 DB::nextId() 创建的。
接下来是一系列函数调用，用于在应用程序的公共表（如 stories 和 authors 表）上设置正常权限，以及在与我们选择授予此用户访问权限的阶段对应的工作流阶段表上设置特定权限。

```
if (empty($user_id))
{
    // if we don't have an ID value, there is no record
    // for this user - create one
    $user_id = db_connect()->nextId('user');
    $query = 'insert into users
    (username, password, name, email, user_id)
    values
    (?,password(?),?,?,?) '
    ;
}
else
{
    // if we have an ID value, a record for this user
    // currently exists in the users table - update it
    $query = 'update users set username=?
    , password=password(?), name=?
    , email=? where user_id = ? '
    ;
}
$stmt = db_connect()->prepare($query);
$bind = array($username,$password,$name,$email,$user_id);
if (!db_connect()->execute($stmt,$bind))
{
    $private_error = db_connect()->last_query;
    user_error('could not update user record', E_USER_WARNING);
    return FALSE;
}
```

回到 user.php 文件，代码接下来将打印出相应的用户信息（如果存在现有用户信息）以及作为一系列复选框的阶段。如果用户对该阶段有权限，则复选框将被选中。

以下查询旨在与先前创建的 checkbox_field() 函数配合使用。该函数接受三个参数（表单名称、值和匹配值）。如果值和 matchvalue 参数匹配，则复选框将被选中。

```
$query = 'select distinct m.stage_id as matchvalue
, s.stage_id, s.stage, s.stage_dsc
from stages s
left join users u on u.user_id = ?
left join user_stage_map m on s.stage_id = m.stage_id
and m.user_id = u.user_id
';
```

此查询收集所有阶段，并对 users 表执行外连接。如果用户已被授予访问某个阶段的权限，则该阶段名称将出现在返回的记录集的 matchvalue 字段中。如果没有，则该字段中会出现一个连字符。当在循环中稍后运行 checkbox_field() 函数时，第三个参数将是一个连字符，或与 stage 字段具有相同的值。此查询的结果可能如下所示：

| matchvalue | stage_id | stage | stage_dsc |
| :--- | :--- | :--- | :--- |
| NULL | 1 | 写作 | 文字 |
| NULL | 2 | 编辑 | 修复错误 |
| 3 | 3 | 发布 | 制作 HTML |
| 4 | 4 | 上线 | 在网络上 |
| 5 | 5 | 已终止 | 已死亡 |

这些知识应该能让你阅读脚本的其余部分。当然，应用程序随附的 CD-ROM 中还包含进一步的注释。

## content/story.php

该脚本大约有 340 行，虽然很长，但并不特别复杂。基于我们之前讨论的数据结构，它需要创建新故事，并在经过编辑审核后更新现有故事。在执行过程中，脚本需要检查用户是否有权处理该故事，并清理用户在表单中输入的文本。

页面内的注释（随附 CD-ROM 提供）应使文件易于阅读。为了使页面正确运行，你需要做出相当多的决策，这也增加了长度。但文件中需要做出的决策相当简单。另外，页面包含相当多的 insert 和 update 语句。在阅读代码时如果参考图 11-8，应该不算太难读完。

本章花了相当大的篇幅讨论如何使用 MySQL 的 GRANT 语句为用户分配权限。希望此时你已经明白这些权限是如何分配的。以下的短脚本测试当前用户是否有权处理某个故事，依据是 grants 表中的权限。它首先根据 stage_id 获取 stage_name，然后通过在阶段名称后追加 _table 来创建表名字符串。接着运行一条包含我们刚刚创建的表名的 SELECT 语句。如果不允许该查询，查询将失败并返回 false。在查询中，我们还涉及 user_stage_map 表。该表提供我们的主要安全保障，用户必须在 user_stage_map 表中拥有当前阶段的权限。如果用户在该表中没有定义的权限，查询将不返回任何行。如果查询失败或不返回任何内容，将打印错误并退出脚本。

```
// if we have an ID value, this is an existing story -
// get information about it from the database

$result = NULL;
if (empty($modify_dt))
{
    // if no timestamp value is passed in, get the
    // current version of the story from the stories
    // table.

    $query = <<<EOO
select m.user_id as is_ok
, s.*
, date_format(s.publish_dt, '%Y') as publish_yr
, date_format(s.publish_dt, '%m') as publish_mn
, date_format(s.publish_dt, '%d') as publish_dy
from stories s
left join user_stage_map m on s.stage_id = m.stage_id
and m.user_id = ?
where s.story_id = ?
EOO;
    $bind = array($user_id,$story_id);
}
else
{
    // if a timestamp is passed in, get the version
    // of the story it identifies from the story_versions
    // table.
    $query = <<<EOO
select m.user_id as is_ok
, s.*
, date_format(s.publish_dt, '%Y') as publish_yr
, date_format(s.publish_dt, '%m') as publish_mn
, date_format(s.publish_dt, '%d') as publish_dy
from story_versions s
left join user_stage_map m on s.stage_id = m.stage_id
and m.user_id = ?
where s.story_id = ? and s.modify_dt = ?
EOO;
    $bind = array($user_id,$story_id,$modify_dt);
}

$result = db_connect()->getRow($query, $bind,
DB_FETCHMODE_ASSOC);

if (!$result['is_ok'])
{
    // if the query has failed, the user has not been
    // granted MySQL select access to the stage
    // access table, and thus does not have permission
    // to edit this story. print out an error and exit.
    print subtitle(
        'You may not edit stories in the '
            . stage($result['stage_id'])
            . ' stage.'
    );
    print end_page();
    exit;
}
```

另一个值得关注的方面是该脚本中进行的大量文本处理。这是一个示例，说明如果我们的用户正在使用某种文本处理工具（例如 HTML 编辑器或文字处理器），我们可能需要进行的处理类型。每种工具都有其自身的一些小特点，我们需要予以考虑。找出我们需要进行的具体清理类型的唯一方法是检查工作场所文本编辑器生成的代码。

例如，我们不希望文章正文中包含完整 HTML 页面的开始和结束标签。因此，如果用户使用所见即所得（WYSIWYG）HTML 编辑器编写了文章，为了更轻松地创建链接等，我们希望剔除页面实际 <BODY> 部分之前和之后的所有内容，并去掉 <BODY> 和 </BODY> 标签本身。

```
$body =
preg_replace('/^.*<body[^>]*>(.*?)</body.*$/i', '$1', $body);
$body = preg_replace('/[\r\n]{1,2}/', "\n", $body);
```

当然，如果你想允许有限的标签集并删除所有其他标签，PHP 的 strip_tags() 函数也可以为你工作。

从 story.php 文件的第 157 行开始——在注释行 "fix up paragraph tags" 处——是一段不错的代码块，它会做几件漂亮的事情。如果用户似乎未使用 <p> 标签输入故事，脚本会在看起来合适的地方添加它们，假设用户使用换行符（硬回车）来指示段落。如果用户确实使用了 <p> 标签，脚本会检查文本，确保没有奇怪的空格或格式错误的标签。我们建议你查看 CD-ROM 上提供的代码和注释，以便很好地了解如何进行复杂的文本处理。
