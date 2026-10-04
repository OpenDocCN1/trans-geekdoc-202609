

# 第7 章

```php
$peoplesql = *SELECT
  FROM
  'people'
;
$result = mysql_query($peoplesql)
or die("Invalid query: " . mysql_error());
while($row = mysql_fetch_array($result , MYSQL_ASSOC)) {
  $people[$row['people_id']] = $row['people_fullname'];
}
```

```php
switch($_GET['action']) {
case 'edit':
  $movies = *SELECT
  FROM
  'movie'
  WHERE
    'movie'.movie_id = '" . $_GET['id'] . '"
  ;
$result = mysql_query($movies)
or die("Invalid query: " . mysql_error());
$row = mysql_fetch_array($result , MYSQL_ASSOC);
$movie_name = $row['movie_name'];
$movie_type = $row['movie_type'];
$movie_year = $row['movie_year'];
$movie_leadactor = $row['movie_leadactor'];
$movie_director = $row['movie_director'];
  break;
default:
  $movie_name = "";
  $movie_type = "";
  $movie_year = "";
  $movie_leadactor = "";
  $movie_director = "";
  break;
}
```

```php
?>
<html>
<head>
<TITLE><?php echo $_GET['action']?> 电影/</TITLE>
</head>
<body>
<form action="commit.php?action=<?php echo $_GET['action']?>&type=movie&id=<?php echo $_GET['id']?>" method="post">
<?php
if (!empty($_GET['error'])) {
  echo "<div align='center' style='color:#FFFFFF;background-color:#ff0000;font-weight:bold!'>" . nl2br(urldecode($_GET['error'])) . "</div><<div><br />";
}
?>
<?php
```

<table border="0" width="750" cellspacing="1" cellpadding="3" bgcolor="#353535" align="center">
  <tr>
    <td bgcolor="#ffffff" width="30%">电影名称</td>
    <td bgcolor="#ffffff" width="70%">
      <input type="text" name="movie_name" value="<?php echo $movie_name?>">
    </td>
  </tr>
  <tr>
    <td bgcolor="#ffffff">电影类型</td>
    <td bgcolor="#ffffff">
      <SELECT id="game" name="movie_type" style="width:150px">
        <option value="">选择一个类型...</option>
<?php
$sql = SELECT \
'motietype_id',
'motietype_label'
FROM
'motietype'
ORDER BY
'motietype_label'
$result = mysqli_query($sql)
 or die(<font color="#FF0000">查询错误</font>.$mysql_error($result)); {
  while ($row = mysqli_fetch_array($result)) {
    if ($row['motietype_id'] == $movie_type){
      $selected = " SELECTED";
    } else {
      $selected = "";
    }
    echo "<OPTION value='$row['motietype_id'].'.$selected.''.$row['motietype_label'].'.</OPTION>";
  }
}
?>
      </SELECT>
    </td>
  </tr>
  <tr>
    <td bgcolor="#ffffff">电影年份</td>
    <td bgcolor="#ffffff">
      <SELECT name="movie_year">
        <option value="">选择一个类型...</option>
<?php
for ($year=date('Y')); $year >= 1970 ; $year-- {
  if ($year == $movie_year){
    $selected = " SELECTED";
  } else {
    $selected = "";
  }
}
?>
        <option value="<?php $year?>"><?php echo $selected?><?php echo $year?></option>
<?php
?>
      </SELECT>
    </td>
  </tr>
  <tr>
    <td bgcolor="#ffffff">主演演员</td>
    <td bgcolor="#ffffff" name="movie_leadactor">
      <option value="SELECTED">选择一个演员...</option>
<?php
foreach ($people as $people_id => $people_fullname) {
    if ($people_id == $movie_leadactor) {
        $selected = " SELECTED";
    } else {
        $selected = " ";
    }
    echo "<option value='$people_id'" . $selected . ">" . $people_fullname . "</option>";
}
?>
<?php
?>
      </SELECT>
    </td>
  </tr>
  <tr>
    <td bgcolor="#ffffff">导演</td>
    <td bgcolor="#ffffff" name="movie_director">
      <option value="SELECTED">选择一个导演...</option>
<?php
foreach ($people as $people_id => $people_fullname) {
    if ($people_id == $movie_director) {
        $selected = " SELECTED";
    } else {
        $selected = " ";
    }
    echo "<option value='$people_id'" . $selected . ">" . $people_fullname . "</option>";
}
?>
<?php
?>?>
      </SELECT>
    </td>
  </tr>
  <tr>
    <td bgcolor="#ffffff" colspan="2" align="center">
      <input type="SUBMIT" name="SUBMIT" value="<?php echo $_GET['action']?>">
    </td>
  </tr>
</table>
</FORM>
</body>
</html>

# 用户输入

2. 保存 movie.php 文件并将其上传到目录。

3. 打开 commit.php 脚本并进行如下修改（**加粗**部分）：

```php
<?php
// 提交与编辑
$error = '';
$link = mysql_connect('localhost', 'root', '') or die("连接失败: " . mysql_error());
mysql_select_db('db', $link) or die(mysql_error());
switch($_GET['action']) {
  case "edit":
    switch ($_GET['type']) {
      case "people":
        $sql = 'UPDATE
          people
          SET
          'people_fullname' = '" . $_POST['people_fullname'] . "',
          WHERE
          'people_id' = '" . $_GET['id'] . '"';
        break;
      case "movie":
        $movie_name = trim($_POST['movie_name']);
        if (empty($movie_name)) {
          $error = "请输入电影名称";
        }
        if (empty($_POST['movie_type'])) {
          $error = "请选择电影类型";
        }
        if (empty($_POST['movie_year'])) {
          $error = "请选择电影年份";
        }
        if (empty($error)) {
          $sql = "UPDATE
            movie
            SET
            'movie_name' = '" . $_POST['movie_name'] . "',
            'movie_year' = '" . $_POST['movie_year'] . "',
            'movie_type' = '" . $_POST['movie_type'] . "',
            'movie_leadactor' = '" . $_POST['movie_leadactor'] . "',
            'movie_director' = '" . $_POST['movie_director'] . "',
            WHERE
            'movie_id' = '" . $_GET['id'] . '"';
        break;
    }
  } else {
    header(
      "location:movie.php?action=edit&error=" . urlencode($error) . "&id=" . $_GET['id']
    );
    break;
  case "add":
    switch ($_GET['type']) {
      case "people":
        $sql = 'INSERT INTO
          'people'
          ('movie_fullname')
        VALUES
          ('" . $_POST['movie_fullname'] .')";
        break;
      case "movie_name":
        $movie_name = trim($_POST['movie_name']);
        if (empty($movie_name)) {
          $error = "请输入电影名称";
        }
        if (empty($_POST['movie_type'])) {
          $error = "请选择电影类型";
        }
        if (empty($_POST['movie_year'])) {
          $error = "请选择电影年份";
        }
        if (empty($error)) {
          $sql = "INSERT INTO
            movie
            ('movie_name',
            'movie_year',
            'movie_type',
            'movie_leadactor',
            'movie_director')
            VALUES
            ('" . $_POST['movie_name'] . "',
            '" . $_POST['movie_year'] . "',
            '" . $_POST['movie_type'] . "',
            '" . $_POST['movie_leadactor'] . "',
            '" . $_POST['movie_director'] . "')";
        } else {
          header("location:movie.php?action=add&error=" . urlencode($error));
        }
        break;
    }
}
if (isset($sql) && !empty($sql)) {
  echo "<!--$sql-->";
  $result = mysql_query($sql);
or die("Invalid query: " . mysql_error());
?>
<p align="center" style="color:#FF0000">
完成。<a href="index.php">首页</a>
</p>
<?php
?>
```

- 4. 将文件保存为 commit.php 并将其到你的服务器。

- 5. 现在打开浏览器访问 http://localhost/chapter7/index.php（根据你的设置调整此 URL），并尝试添加一个没有名称的电影，如图 7-3 所示。

![](img/7b817c5b51395bdcaba58e6a2bc6daa_221_0.png)

图 7-3

- 6. 现在尝试输入一部新电影，但不设置年份和类型（见图 7-4）。

- 7. 从首页编辑电影，并尝试删除名称后提交表单（见图 7-5）。

- 8. 注意说明填写表单时错误的错误信息（图 7-6）。

# 用户输入验证

| | |
|------|
| 电影名称 | 某些电影 |
| 电影类型 | 选择一个类型... |
| 电影年份 | 选择一个年份... |
| 主演演员 | Jim Carney |
| 导演 | Ron Livingston |
| 电影发布日期 (dd-mm-yyyy) | 29-10-2003 |
| 电影评分 (0 到 10) | |

图 7-4

