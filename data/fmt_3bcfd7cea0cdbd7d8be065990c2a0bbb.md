
图 9-2 显示了日程视图（Schedule View）的一个示例。

#### 图 9-2. `meeting.pgp`—查看日程

![graphics/09fig02.jpg](img/09fig02.jpg)

#### 脚本 9-2. `meeting.php` 逐行解释

| 行号 | 描述 |
| --- | --- |
| 2–231 | 定义函数 `addmeetingwizard()`，引导用户完成会议创建。该函数接受一个参数，即向导的当前步骤。 |
| 3 | 启动会话以存储向导所需的变量。 |
| 4 | 打印页面 HTML 的起始部分。我们需要在 `session_start()` 函数之后执行此操作，因为已经向页面输出了文本，会话将无法工作。 |
| 5 | 定义脚本中使用的某些全局变量。 |
| 6 | 创建一个 `switch` 语句。`switch` 语句中的每个 `case` 对应于向导中的一个步骤。 |
| 7–27 | 开始向导的第一步。在这里我们询问用户会议名称以及会议持续时间。使用隐藏表单字段，以便在用户提交表单时将他们引导到下一步。 |
| 28–87 | 开始向导的第二步。此步首先检查用户是否输入了会议名称。如果没有输入名称，则将用户送回第一步。如果用户输入了名称，脚本将创建一个名为 `$fields` 的数组，用于存储会议的值。脚本还会获取用户 ID 并将其作为会议发起者存入 `$fields` 数组中。然后，它将会议名称和时间添加到 `$fields` 数组中。使用 `meetingdisplay()` 函数在屏幕上显示已输入的信息。脚本接着确定哪些房间可用，并列出空闲房间以及“虚拟”房间。一旦用户选择了房间，脚本将进入第三步。 |
| 88–144 | 开始向导的第三步。确定哪些用户已经安排了会议，并将他们列入列表中，并在名字旁边标注“(忙碌)”。一旦用户选择了参与者，继续继续到第四步。 |
| 145–173 | 开始向导的第四步。验证是否至少选择了一个用户作为参与者。如果没有选择参与者，则将用户送回第三步。如果至少选择了一个参与者，则提供一个表单，让用户输入会议议程、电话号码和网站。 |
| 174–197 | 开始向导的第五步。验证议程是否已填写。如果没有填写，则将用户送回第四步。如果议程已填写，则提供一个按钮让用户可以完成会议。 |
| 198–215 | 将会话 `$fields` 数组中的值输入数据库，并调用 `notifyuser()` 函数向所有受邀参与者发送电子邮件。 |
| 216–229 | 为 `switch` 提供一个默认 `default` 情况，以防发生任何情况导致函数跳过其他 `case`。向用户打印错误信息。 |
| 230 | 关闭在第 6 行开始的 `switch` 语句！ |
| 231 | 结束 `addmeetingwizard()` 的函数声明。 |
| 233–266 | 定义函数 `meetingdisplay()`，在用户通过会议创建向导时显示会议详情。由于 `$fields` 数组在每一步中都会添加项，因此我们只显示用户输入的信息。 |
| 268–315 | 定义函数 `viewschedule()`，允许用户在表格中一次查看他们所有的会议。该函数还提供了一个链接，使用户可以查看会议的完整详情，或者如果他们是发起者，提供取消会议的链接。 |
| 318–348 | 定义函数 `view_meeting_details()`，允许用户查看特定会议的完整详情。 |
| 350–379 | 定义函数 `deletemeeting()`，从数据库中删除会议，并通过电子邮件通知所有参与者会议已取消。 |
| 381–403 | 定义函数 `notifyusers()`，发送电子邮件通知用户他们被邀请参加新会议。 |
| 405–427 | 定义函数 `check_user()`，验证用户登录。这与第 7 章中使用的函数相似。 |
| 429–439 | 定义函数 `login()`，打印一个允许用户登录的表单。 |
| 441–447 | 定义函数 `choices()`，允许用户查看他们的日程或安排新会议。 |
| 449 | 开始主程序。 |
| 450 | 定义 `$page` 变量，用于那些带有表单的函数。 |
| 451 | 引入 `meeting_inc.php` 脚本，因为它包含了此脚本使用的函数。 |
| 452–453 | 检查用户是否已登录。如果没有，调用 `login()` 函数让用户登录。 |
| 454–456 | 如果用户已登录且 `$addmeeting` 变量已设置，则说明用户正在会议创建向导的中间。将用户送回向导。 |
| 457–479 | 如果用户已登录且 `$action` 变量已设置，则说明用户正在开始或完成特定任务。根据执行的操作将用户发送相应的函数。 |
| 480–483 | 如果用户已登录但没有创建会议或执行其他任务，则提供一些可以使用 `choices()` 函数的选项。 |
| 484 | 关闭在第 452 行开始的 `if` 语句。 |
| 486 | 结束页面的 PHP。 |
| 487–488 | 结束页面的 HTML。 |

#### `meeting_inc.php`

`meeting_inc.php` 包含了 `meeting.php` 和 `admin.php` 使用的代码。

##### 脚本 9-3 `meeting_inc.php`

```php
1.  <?
 2.
3.  /***** FUNCTIONS *****/
 4.  function connect() {
 5.    ini_set("include_path", "G:\apache\Apache\php\pear");
 6.    require_once("DB.php");
 7.    $type = "mysql";
 8.    $username = "php";
 9.    $password = "password";
10.    $host = "localhost";
11.    $database = "meeting";
12.    $dsn = $type . "://" . $username . ":" . $password . "@" . $host . "/" . $database;
13.    $dbconn = DB::connect($dsn);
14.    errortrap($dbconn);
15.    $dbconn->setFetchMode(DB_FETCHMODE_ASSOC);
16.    return $dbconn;
17.  }//end connect
18.
19.  function errortrap($result) {
20.    if(DB::isError($result)) {
21.      ?><h3>There was an error!</h3><?
22.      die($result->getMessage());
23.    }
24.  } //end errortrap
25.
26.  function datafromid($dbconn, $table, $id) {
27.    $sql = "select * from $table where id = '$id'";
28.    $result = $dbconn->query($sql);
29.    errortrap($result);
30.    $result->fetchInto($row);
31.    return $row;
32.  } //end datafromid
33.
34.  function createdate($type) {
35.    $years = array("2002","2003","2004");
36.    $minutes = array(":00", ":15", ":30", ":45");
37.    $months = array();
38.    $days = array();
39.    $hours = array();
40.    for($i = 1; $i < 13; $i++) {
41.      if($i < 10) {
42.        $months[] = "0" . $i;
43.      } else {
44.        $months[] = $i;
45.      }
46.    }
47.    for($i = 1; $i < 32; $i++) {
48.      if($i < 10) {
49.        $days[] = "0" . $i;
50.      } else {
51.        $days[] = $i;
52.      }
53.    }
54.    for($i = 1; $i < 25; $i++) {
55.      $hours[] = $i;
56.    }
57.    $fields = array("years", "months", "days", "hours", "minutes");
58.    foreach($fields as $field) {
59.      ?>
60.      <select name="<? echo $type . $field ?>">
61.      <?
62.        foreach($$field as $item) {
63.          echo"<option value=$item>$item</option>\n";
64.        }
65.      ?>
66.      </select>
67.      <?
68.      if($field == "days") {
69.        echo " at ";
70.      }
71.    }
72.  } //end createdate
73.
74.  function head() {
75.    ?>
76.    <html
77.    <head>
78.    <style type=text/css>
79.    h1, h2, h3, p, td, li {font-family: verdana, sans-serif; }
80.    </style>
81.    </head>
82.    <body bgcolor="#FFFFFF">
83.    <div align=center>
84.    <table width="74%" border="0" cellspacing="0" cellpadding="0" height="128" 
85.bgcolor="#FFFFFF">
86.        <tr>
87.          <td height="134" align="center"><h1>A Meeting Manager</h1></td>
88.        </tr>
89.      </table
90.    </div
91.    <?
92.  }
93.  ?>
```

##### 脚本 9-3. `meeting_inc.php` 逐行解释

| 行号 | 说明 |
| --- | --- |
| 4–17 | 定义一个函数 `connect()`，用于建立与数据库的连接。请确保更改这些值以匹配你的特定设置。 |
| 19–24 | 定义一个函数 `errortrap()`，用于捕获可能任何 PEAR DB 错误。 |
| 26–32 | 定义一个函数 `datafromid()`，根据 `id` 从特定表中选择所有信息。该函数在整个脚本中使用，并减少了大量的输入工作。 |
| 34–72 | 定义一个函数 `createdate()`，为日期创建一个美观的下拉菜单。 |
| 74–91 | 定义一个函数 `head()`，用于打印任何页面的 HTML 头部。 |
| 92 | 结束脚本的 PHP。 |

图 9-4 显示了创建会议向导的示例。

##### 图 9-4. `meeting.php`—创建向导

`admin.php` 是该应用程序的管理界面。

##### 脚本 9-4 `admin.php`
