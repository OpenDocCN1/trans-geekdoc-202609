

```php
if(!$os) {
    $query = "INSERT INTO useragent VALUES (NULL, '$useragent')";
    if($mysql_query($query)) exit(mysql_error());
}
?>
```

```php
$query = "INSERT INTO useragent VALUES (NULL, '$useragent')";
    if($mysql_query($query)) exit(mysql_error());
}
?>
```

现在，通过分析 `useragent` 表，可以确定该网站是否被搜索引擎机器人访问过。

## II.6.6. 防止下载管理器下载

考虑一种流行的下载管理器，其用户代理（user agent）具有如下的格式：

-   Teleport Pro/1.29

要实现既定目标，只需将列表 II.6.10所示所示字符串放在页面开头即可。

列表 II.6.10. 防止下载管理器

```php
<?php
if(substr($_SERVER['HTTP_USER_AGENT'], 0, 8) == "Teleport") exit();
?>
```

防止下载管理器非法下载网站内容的方法并不是通用的。因为 `$_SERVER['HTTP_USER_AGENT']` 字符串是由客户端生成的——确切地说，是由主要目标是不计代价下载页面的下载管理器生成的——这个字符串经常被伪造，甚至留为空。

![](img/a893312ec68b8170fe567f785e95c06e_270_0.png)

注意

## II.6.7. 伪造用户代理

要伪造用户代理，需要伪造 User-Agent 头部。例如，一个 Windows XP 用户可能会有如下用户代理：

```
Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
```

## 列表 II.6.11. 构造伪造的用户代理

```php
<?php
$hostname = "host";
$path = "/path/index.php";
$line = "";

// 建立连接，其 hostname 参数
// 通过 $hostname 参数传递进来
$fp = fsockopen($hostname, 80, $errno, $errstr, 30);
// 检查连接是否成功建立
if (!$fp) echo $errstr ($errno)<br />

else {
    // 构建用于传输到
// 服务器的 HTTP 头部
    $headers = "GET $path HTTP/1.1\r\n";
    $headers .= "Host: $hostname\r\n";
    // 伪造用户代理
    // 伪装成 Windows XP 用户
    $headers .= "User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1\r\n";
    $headers .= "Connection: Close\r\n";
    // 向服务器发送 HTTP 请求
    fwrite($fp, $headers);
    // 接收响应
    while (!feof($fp)) {
        $line = fgets($fp, 1024);
    }
    fclose($fp);
}
echo $line;
?>
```

# 第 II.7 章：授权与认证

![](img/a893312ec68b8170fe567f785e95c06e_272_0.png)

## II.7.1. 基于文件的授权

在输入用户名和密码后，将检查用户名是否列在 `text.txt` 文件中。如果检查结果为正，则用户提供的密码与文件中存储的与用户名相关的密码进行比较。如果匹配，则显示编辑数据的表单。相应的脚本在列表 II.7.1所示。

列表 II.7.1. 基于文件的授权

```php
<?php
// 数据文件名
$filename = "text.txt";
// 定义第一个常量
// 用来判断
// 1.php 文件是否已执行
define("FIRST", 1);
// 检查 $_POST 数组
// 是否为空。如果是，则显示
// 授权表单
if (empty(\$_POST)) {
  <<table>
    <form method="post">
      <tr>
        <td>登录：</td>
        <td><input type="text" name="name"></td>
      </tr>
      <tr>
        <td>密码：</td>
        <td><input type="password" name="pass"></td>
      </tr>
      <tr>
        <td>&nbsp;</td>
        <td><input type="submit" value='进入'></td>
      </tr>
    </form>
  </table>
}
?>
<?php
// 如果 POST 数据已
// 发送，则处理它们
else {
  // 验证输入的
// 用户名和密码
  $arr = file(\$filename);
  $i = 0;
  $temp = array();
  foreach($arr as $line) {
    // 以 :: 分隔符分割行
    $data = explode(":", $line);
    // 将已注册用户的
// 用户名放入 $data 数组中
    $temp['name'][\i] = \$data[0];
    $temp['password'][\i] = \$data[1];
    $temp['email'][\i] = \$data[2];
    $temp['url'][$i] = trim($data[3]);
    // 计数器加1
    $i++;
  }
// 如果输入的登录名不在
// $temp['name'] 数组中，则终止脚本
if(!in_array($_POST['name'],$temp['name']))
{
    exit("无此用户!");
}
// 如果输入的登录名在 $_POST['name'] 数组中，
// 验证密码
$index = array_search($_POST['name'],$temp['name']);
if($_POST['password'] != $temp['password'][$index])
{
    exit("密码错误!");
}
// 如果输入正确的密码，
// 显示编辑数据的表单
include "2.php"; // 第二个 HTML 表单的处理器。
?>
```

<table>
<form method="post">
<input type="hidden" name="name"
value="<?php htmlspecialchars($temp['name']][$index]); ?>"
<input type="hidden" name="pass"
value="<?php htmlspecialchars($temp['password']][$index]); ?>"
<input type="hidden" name="edit" value="edit">
<tr>
<td>邮箱：</td>
<td><input type="text" name="email" value="<?php htmlspecialchars($temp['email']][$index]); ?></td>
</tr>
<tr>
<td>URL：</td>
<td><input type="text" name="url" value="<?php htmlspecialchars($temp['url']][$index]); ?></td>
</tr>
<tr>
<td>&nbsp;</td>
<td><input type="submit" value="编辑"></td>
</tr>
</form>
</table>
<?php
// 如果 1.php 文件中的
// FIRST 常量未定义，则尝试
// 绕过文件。阻止这种尝试
if (!defined('FIRST')) exit();
// 如果传递了 $_POST['edit'] 参数，
// 说明表单用于编辑数据。
if($_POST['edit'] == 'edit')
{
// 数据验证块
// 去除额外的空格
$_POST['name'] = trim($_POST['name']);
$_POST['pass'] = trim($_POST['pass']);
$_POST['pass_again'] = trim($_POST['pass_again']);
// 检查 $_POST 数组是否为空
if (empty($_POST['name'])) exit();
// 验证必需字段是否正确填写
if($_POST['name']) != exit('“用户名”字段不能为空!');
if (empty($_POST['pass']))
exit('“密码”字段不能为空!');
if (empty($_POST['pass_again']))
exit('“确认密码”字段不能为空!');
if($_POST['pass'] != $_POST['again'])
exit('密码不匹配!');
// 如果提供了邮箱，验证其格式
if(!empty($_POST['email']))
{
if(!preg_match("^[0-9a-z_]+@[0-9a-z_]+\.[a-z]{2,6}$/i", 
	$_POST['email']))
{
	exit
	('邮箱地址必须符合 somebody@somewhere.ru 格式。');
}
}
// 编辑数据文件
$arr = file($filename);
$linefile = array();
foreach($arr as $line) {
```
