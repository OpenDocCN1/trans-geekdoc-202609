
"memberId" => "",
"pageUrl" => "",
"numVisits" => "",
"lastAccess" => ""
);
public static function getLogEntries( $memberId ) {
$conn = parent::connect();
$sql = "SELECT * FROM " . TBL_ACCESS_LOG . " WHERE memberId = :memberId ORDER BY lastAccess DESC";
try {
$st = $conn->prepare( $sql );
$st->bindValue( ":memberId", $memberId, PDO::PARAM_INT );
$st->execute();
$logEntries = array();
foreach ( $st->fetchAll() as $row ) {
$logEntries[] = new LogEntry( $row );
}
parent::disconnect( $conn );
return $logEntries;
} catch ( PDOException $e ) {
parent::disconnect( $conn );
die( "Query failed: " . $e->getMessage() );
}
}
?>

与 Member 类一样，LogEntry 类派生自 DataObject 抽象类。其受保护的 $data 数组包含 accessLog 表中的字段名：memberId、pageUrl、numVisits 和 lastAccess。

LogEntry 只包含一个方法 getLogEntries()，用于检索特定成员（由 $memberId 指定）的所有 accessLog 记录，并以 LogEntry 对象形式返回。查询按访问日期降序排列条目，即最新的记录排在前面：

```
$sql = "SELECT * FROM " . TBL_ACCESS_LOG . " WHERE memberId = :memberId ORDER BY lastAccess DESC";
```

该方法的其余部分与 Member::getMembers() 类似。预处理语句，将 $memberId 参数绑定到 :memberId 占位符，并执行查询。使用 PDOStatement::fetchAll() 将记录集检索为关联数组数组，每个关联数组用于创建一个新的 LogEntry 对象，然后将其添加到数组中。该方法随后将 LogEntry 对象数组返回给调用代码。

## 创建 view_members.php 脚本

现在，你已为会员查看器应用程序奠定了所有基础；事实上，你已经完成了大部分艰苦的工作。现在只需编写两个脚本：一个用于显示会员列表，另一个用于显示单个会员的详细信息。

首先是会员列表。将以下代码保存为 book_club 文件夹中的 view_members.php：

```
<?php

require_once( "common.inc.php" );
require_once( "config.php" );
require_once( "Member.class.php" );

$start = isset( $_GET["start"] ) ? (int)$_GET["start"] : 0;
$order = isset( $_GET["order"] ) ? preg_replace( "/[^a-zA-Z]/", "",
$_GET["order"] ) : "username";
list( $members, $totalRows ) = Member::getMembers( $start, PAGE_SIZE,
$order );
displayPageHeader( "View book club members" );

?>
<h2>Displaying members <?php echo $start + 1 ?> - <?php echo min( $start +
PAGE_SIZE, $totalRows ) ?> of <?php echo $totalRows ?></h2>

<table cellSpacing="0" style="width: 30em; border: 1px solid #666;">
<tr>
<th><?php if ( $order != "username" ) { ?><a href="view_members.php?
order=username"><?php } ?>Username<?php if ( $order != "username" )
{ ?></a><?php } ?></th>
<th><?php if ( $order != "firstName" ) { ?><a href="view_members.php?
order=firstName"><?php } ?>First name<?php if ( $order != "firstName" )
{ ?></a><?php } ?></th>
<th><?php if ( $order != "lastName" ) { ?><a href="view_members.php?
order=lastName"><?php } ?>Last name<?php if ( $order != "lastName" )
{ ?></a><?php } ?></th>
</tr>
<?php
$rowCount = 0;

foreach ( $members as $member ) {
$rowCount++;
?>
<tr><?php if ( $rowCount % 2 == 0 ) echo ' class="alt"' ?>>
<td><a href="view_member.php?memberId=<?php echo $member->
getValueEncoded( "id" ) ?>"><?php echo $member->
getValueEncoded( "username" ) ?></a></td>
<td><?php echo $member->getValueEncoded( "firstName" ) ?></td>
<td><?php echo $member->getValueEncoded( "lastName" ) ?></td>
</tr>
<?php
}
?>
</table>

<div style="width: 30em; margin-top: 20px; text-align: center;">
<?php if ( $start > 0 ) { ?>
<a href="view_members.php?start=<?php echo max( $start - PAGE_SIZE, 0 )
?&amp;order=<?php echo $order ?>">Previous page</a>
<?php } ?>
&nbsp;
<?php if ( $start + PAGE_SIZE < $totalRows ) { ?>
    <a href="view_members.php?start=<?php echo min( $start + PAGE_SIZE,
        $totalRows ) ?&amp;order=<?php echo $order ?>">Next page</a>
<?php } ?></div>

<?php
    displayPageFooter();
?>
```

此脚本使用 Member 类从数据库中检索会员列表，然后在页面上显示该列表。它首先检索两个查询字符串参数——start，表示开始在页面上显示记录的记录位置，以及 order，用于指定按哪一列对数据进行排序——并将参数值存储在两个变量 $start 和 $order 中。如果未向脚本传递其中任何参数，则使用默认值。为提高安全性，脚本会过滤这两个参数以确保其包含有效值：$start 被强制转换为 int，而 $order 使用正则表达式删除任何非字母字符（因为会员表中的字段名仅使用字母）。

*你可以在第 18 章中了解有关正则表达式的更多信息。*

接下来，脚本检索要在页面上显示的会员列表。执行此操作的代码非常简单，因为所有复杂性都被很好地隐藏在 Member 类中：

```
list( $members, $totalRows ) = Member::getMembers( $start, PAGE_SIZE, $order );
```

调用 Member::getMembers()，传入开始检索记录的行、要检索的记录数以及用于 ORDER BY 子句的字符串。getMembers() 乖乖返回一个两个元素的数组。第一个元素——Member 对象列表——存储在 $members 中，第二个元素——members 表中的会员总数——存储在 $totalRows 中。

检索数据后，只需在页面上显示列表即可。首先，调用 displayPageHeader() 并传入适当的页面标题以显示 XHTML 标头。然后启动一个 XHTML 表格元素，包含三个标题单元格，分别对应用户名、名和姓：

```
<th><?php if ( $order != "username" ) { ?><a
href="view_members.php?order=username"><?php } ?>Username<?php if ( $order != "username" ) {
{ }</a><?php } ?></th>
<th><?php if ( $order != "firstName" ) { ?><a
href="view_members.php?order=firstName"><?php } ?>First name<?php if ( $order != "firstName" ) {
{ }</a><?php } ?></th>
<th><?php if ( $order != "lastName" ) { ?><a
href="view_members.php?order=lastName"><?php } ?>Last name<?php if ( $order != "lastName" ) {
{ }</a><?php } ?></th>
```

在此，每个列名都链接到一个 URL，访问该 URL 会重新运行 view_members.php 并传入新的 order 查询参数，以按该列对数据进行排序。但是，如果数据已按某个特定列排序，则该列名不作为链接，以指示数据已按该列排序。

## 第三部分：在实践中使用 PHP

接下来，按每行表格一条记录的方式输出数据：

```
<?php
$rowCount = 0;

foreach ( $members as $member ) {
$rowCount++;
?>
<tr><?php if ( $rowCount % 2 == 0 ) echo ' class="alt"' ?>>
<td><a href="view_member.php?memberId=<?php echo $member->
getValueEncoded( "id" ) ?>"><?php echo $member->
getValueEncoded( "username" ) ?></a></td>
<td><?php echo $member->getValueEncoded( "firstName" ) ?></td>
<td><?php echo $member->getValueEncoded( "lastName" ) ?></td>
</tr>
<?php
}
?>
```

对于每一行，脚本在单独的表格单元格中显示当前会员的三个字段值——用户名、名和姓。对于每个单元格，会调用 Member 对象的 getValueEncoded() 方法，以获取经过特殊 XHTML 字符编码的适当字段值。此外，用户名单元格中的值会链接到 view_member.php 脚本（你稍后将创建该脚本），并传入应显示其详细信息的会员 ID。

$rowCount 用于跟踪当前行号。如果该数字为偶数，则将表格行的 CSS 类设置为 alt，从而产生页面标头中 CSS 定义的交替行效果。

脚本的最后一部分生成用于跳转到上一页和下一页会员的链接：

```
<div style="width: 30em; margin-top: 20px; text-align: center;">
<?php if ( $start > 0 ) { ?>
 <a href="view_members.php?start=<?php echo max( $start - PAGE_SIZE, 0 )
?>&amp;order=<?php echo $order ?>">Previous page</a>
<?php } ?>
&nbsp;
<?php if ( $start + PAGE_SIZE < $totalRows ) { ?>
 <a href="view_members.php?start=<?php echo min( $start + PAGE_SIZE,
$totalRows ) ?>&amp;order=<?php echo $order ?>">Next page</a>
<?php } ?>
</div>
```

如果当前页不是会员列表的开头（$start > 0），则会创建“上一页”链接。该链接指向同一个 view_members.php 脚本，并传入比当前值少一页的新 start 值。（如果新的 start 值恰好为负数，则将其设置为零。）

同样，如果当前页不是会员列表的最后一页（$start + PAGE_SIZE < $totalRows），则会创建“下一页”链接，将 start 设置为比当前 start 值大一页（如果 start 最终会大于 $totalRows，则为 $totalRows）。

请注意，两个链接还会传递 order 查询字符串参数，以确保跨页保持正确的排序顺序。
