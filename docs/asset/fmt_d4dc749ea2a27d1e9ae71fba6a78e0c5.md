
# 10. 输入 `login.php`，即登录页面。猜猜它是做什么用的？

```php
<?php require_once 'header.php'; ?>
<form name="theForm" method="post" action="transact-user.php">
<h3>会员登录</h3>
<p>
  邮箱地址:<br />
  <input type="text" name="email" maxlength="255" value="<?php
echo $_GET['e']; \?>" />
</p>
<p>
  密码:<br />
  <input type="password" name="passwd" maxlength="50" />
</p>
<p>
  <input type="submit" name="submit" value="登录" />
</p>
<p>
  还没有会员吗？ <a href="useraccount.php">创建一个新账户！</a>
</p>
<p>
  <a href="forgotpass.php">忘记密码了？</a>
</p>
</form>
<?php require_once 'footer.php'; ?>
```

# 11. 创建 `forgotpass.php`。如果用户忘记或丢失了密码，将显示此页面。

```php
<?php require_once 'header.php'; ?>
<form method="post" action="transact-user.php">
<h3>邮箱获取密码</h3>
<p>
  忘记密码了？只需输入地址，我们将通过邮箱将密码发送给您！</p>

邮箱地址:<br />
<input type="text" id="email" name="email" />
<input type="submit" class="submit" name="action" value="发送!" />
</form>
<?php require_once 'footer.php'; ?>
```

# 12. 输入 `admin.php`：这是编辑不同板块属性、用户信息、论坛的页面。

```php
<?php
require_once 'header.php';
?>

<script type="text/javascript">
function deleteBBCode(id) {
  window.location = "transact-admin.php?action=deleteCode&b=" + id;
}
function deleteForum(id) {
  window.location = "transact-admin.php?action=deleteForum&f=" + id;
}
</script>
```

```php
<?php

$sql = "SELECT * FROM forum";

$result = mysql_query($sql) or die(mysql_error());

while ($row = mysql_fetch_array($result)) {

  echo '<tr><td><span class='forumname'>" . $row['forum_name'] . "</span>

  <br><span class='forumdesc'>" . $row['forum_desc'] . "</span></td>

  <td><a href='editform.php?forum=' . $row['id'] . "'>编辑</a></td>

  <td><a href='#' onclick='deleteForum(' . $row['id'] . ")'>删除</a></td></tr>';

}

?>

</table>

<p class='buttonBar'>

<a href='editform.php' class='buttonlink'>新论坛</a>

</p>
```

```php
<?php
break;
'bbcode':
?>
<h3>BBcode 管理</h3>
<form id='bbcodeForm' method='post' action='transact-admin.php'>
<table cellspacing='0' class='formtable'>
<tr>
<th>模板</th>
<th>替换</th>
<th>操作</th>
</tr>
<?php
if (isset($bbcode)) {
  foreach ($bbcode as $k => $v) {
    echo '<tr><td>
    <input class='mono' type='text' name='bbcode_t.' . $k . '
    value=' . $v['template'] . "' size='32'></td>
    <td>
    <input class='mono' type='text' name='bbcode_r.' . $k . '
    value=' . $v['replacement'] . "' size='32'></td>
    <td>
    <input type='button' class='submit' value='删除'
    name='action' id='delBBcode' onclick='deleteBBCode(' . $k . ")'></td></td></tr>';
  }
}
?>
<tr class='row2'><td colspan='3'>&nbsp;</td></tr>
<tr class='row2'><td>
<input class='mono' type='text' name='bbcode-new' size='32'></td><td>
<input class='mono' type='text' name='bbcode-r-new' size='32'></td><td>
<input type='submit' class='submit' name='action'
id='addBBcode' value='添加新的'></td></tr>
</table>
<p class='buttonBar'>
?>
```

```php
<input class='submit' type='submit' name='action'

Id='Update' value='更新 Bcodes'>

</p>

</form>

<?php

break;

default:

}

</script>

<?php require_once 'footer.php'; ?>
```

# 13. 创建 `account.php`。用户访问此页面编辑个人资料。

```php

value="<?php echo htmlspecialchars($usemail); ?>" />

<?php

<?php

}

if ($mode == "Modify") {

echo "<fieldset>";

echo "<legend>权限级别</legend>";

$sql = "SELECT * FROM access_levels ORDER BY access_lvl DESC;";

$result = mysql_query($sql, $conn)

or die('Could not list access levels: ' . mysql_error());

while ($row = mysql_fetch_array($result)) {

echo "<input type='radio' class='radio' id='acl_"

" . $row['access_lvl'] . " name='accesslvl' value='"

" . $row['access_lvl'] . "'>";

if ($row['access_lvl'] == $accesslvl) {

echo "checked";

}

echo "/>" . $row['access_name'] . "<br />";

}

echo "</fieldset></div>";

if ($mode == "Modify") echo "<div>";

```

# 14. 输入 `editforum.php`，用于编辑论坛详情：

```php

<?php

if (isset($_GET['forum'])) {

$Action="Edit";

} else {

$Action="Add";

}

$pageTitle = "动作论坛";

require_once 'header.php';

$forum = 0;

$fname = '';

$fdesc = '';

$fmod = '';

$userid = 0;

if (isset($_GET['forum'])) {

$forum = $_GET['forum'];

$sql = "SELECT forum_name, forum_desc, u.name, u.id 

FROM forum_f f

LEFT JOIN forum_users u

ON f.moderator = u.id 

WHERE f.id = $forum";

$result = mysql_query($sql) or die(mysql_error());

if ($row = mysql_fetch_array($result)) {

$fname = $row['forum_name'];

$fdesc = $row['forum_desc'];

$fmod = $row['name'];

$userid = $row['id'];

}

}

?>

echo "<h2>" . $Action . "</h2>";

?>

<form name="editforum" action="transact-admin.php" method="post">

<table class="formtable cellspacing='0'>

<tr><th colspan='2'>通用论坛设置</th></tr>

<tr>

<td>论坛名称</td>

</tr>

<td></td>

</td>

```
## 创建公告板系统 (BBS)

```php

<input type='text' name='forumname'

  value="<?php echo $fname;?>"

)</td>

<tr>

<td>表单描述</td>

<td>

  <input type='text' name='formdesc' size='75'

  value="<?php echo $fdesc;?>"

)</td>

</tr>

<tr

<td>论坛版主（审核员）</td>

<td>

  <select id='moderator' name='forummod[]'>

  <option value='0'>未审核</option>

  <?php

  $sql = 'SELECT * FROM forum_users \

  WHERE access_lvl = 1';

  $result = mysql_query($sql);

  while ($row = mysql_fetch_array($result)) {

    echo '<option value=''.$row['id'].'">';

    if ($userid == $row['id']) echo ' selected="selected"';

    echo ''>'.$row['name'].'</option>';

  }

  ?>

  </select>

</td>

</tr>

<tr

<td colspan='2'>

  <input class='submit' type='submit' name='action'

  value="<?php echo $action; ?>论坛"

</td>

</tr>

</table>

</td>

```

# 15. 创建 `viewtopic.php`，用于显示线程中所有的帖子：

```php

<?php

require_once 'conn.php';

require_once 'functions.php';

require_once 'http.php';

if (isset($_GET['t'])) redirect('index.php');

require_once 'header.php';

$topicid = $_GET['t'];

$limit = $admin['pageLimit']['value'];

showTopic($topicid,TRUE);

require_once 'footer.php';

?>
```

# 第 15 章

## 16. 创建 `viewform.php`，用于显示论坛下的所有主题（话题）：

```php

<?php

require_once 'conn.php';

require_once 'functions.php';

require_once 'http.php';

if (isset($_GET['f'])) redirect('index.php');

require_once 'header.php';

$forumid = $_GET['f'];

$forum = getForum($forumid);

echo breadcrumb($forumid, "论坛*");

if (isset($_GET['page'])) {

$page = $_GET['page'];

} else {

$page = 1;

}

$limit = $admin['pageLimit']['value'];

if ($limit == '') $limit = 25;

$start = ($page - 1) * $admin['pageLimit']['value'];

$sql = "CREATE TEMPORARY table tmp (\n  topic_id INT(11) NOT NULL DEFAULT 0,\n  postdate datetime NOT NULL DEFAULT '0000-00-00 00:00:00'\n);";

mysql_query($sql) or die(mysql_error().'<br>"..$sql);

$sql = "LOCK TABLES forum_users READ, forum_posts READ";

mysql_query($sql) or die(mysql_error().'<br>"..$sql);

$sql = "INSERT INTO tmp SELECT topic_id,MAX(date_posted) \n  FROM forum_posts \n  WHERE forum_id = $forumid \n  AND topic_id > 0 \n  GROUP BY topic_id";

mysql_query($sql) or die(mysql_error().'<br>"..$sql);

$sql = "UNLOCK TABLES";

mysql_query($sql) or die(mysql_error().'<br>"..$sql);

//('stop');

$sql = "SELECT SQL_CALC_FOUND_ROWS *\n  t.topic_id as topic_id, t.subject as t_subject,\n  u.name as t_author, count(p.id) as replies,\n  t.date_posted as t_posted, tmp.postusers as re_posted \n  FROM forum_users u \n  JOIN forum_posts t \n  ON t.author_id = u.id \n  LEFT JOIN tmp \n  ON t.topic_id = tmp.topic_id \n  LEFT JOIN forum_posts p \n  ON p.topic_id = t.topic_id \n  WHERE t.forum_id = $forumid \n  AND t.topic_id = 0 \n  GROUP BY t.topic_id";

require_once 'footer.php';

?>
```

## 17. 进入 `compose.php`，该页面用于输入帖子标题和正文的表单：

```php

<?php

require_once 'conn.php';

require_once 'functions.php';

require_once 'header.php';

$subject = '';

$topicid = $_GET['topicid'];

$forumid = $_GET['forumid'];

$reid = $_GET['reid'];

$body = '';

$post = '';

$authorid = $_SESSION['user_id'];

$edit_mode=FALSE;

if (isset($_GET['a'])

and $_GET['a'] == 'edit'

and isset($_GET['post'])

and $_GET['post']) {

$edit_mode=TRUE;

}

require_once 'header.php';

if (!isset($_SESSION['user_id']) != $_authorized) {

echo "<div class=\"note\">\n你必须登录才能发帖。请在发帖前 <a href=\"login.php\">登录</a>。</div>";
```
