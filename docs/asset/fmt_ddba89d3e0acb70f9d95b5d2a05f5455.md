
*   Core PHP: Using PHP by Prentice Hall

你不应该将会话文件（session files）存储在任何从 Web 服务器可见的目录中。如果你使用的是 `Apache`，那么任何 `htdocs` 目录下的目录都是如此。你不希望将会话文件放置在 Web 服务器可见的目录中的，是因为恶意用户可能会打开这些文件并查看单个会话数据，甚至通过这种方式劫持用户会话。

## 启动会话

除非你在每个想要使用或更改变量的页面上启动会话，否则你无法跨用户会话跟踪变量。启动会话使用 `session_start()` 函数：

```
session_start();
```

`session_start()` 不接受任何参数。如果你正在启动一个新的会话，该函数将初始化会话并创建必要的临时文件来跟踪会话。如果函数通过 cookie 或 `GET` 变量发现了 `$PHPSESSID`，则函数将恢复当前会话，页面将可以任何已注册到会话的变量。

一旦你启动了会话，你就需要向会话注册一些变量。在通过 `session_register()` 函数注册变量之前，会话不会跟踪这些变量：

```
session_register(STRING);
```

`session_register()` 的 `STRING` 参数应该是你想注册到会话的变量名称，以便可以在任何启用会话的页面上访问它。

一旦你启动了会话并注册了一个或多个变量，你就可以在网站的任何启用会话的页面使用这些变量。脚本 2-1 `session.php` 提供了一个启动会话和注册变量的简单示例。

### 脚本 2-1 session.php

```
1.  <?
2.  session_start();
3.  if(!isset($count)) {
4.    session_register("count");
5.    $count = 1;
6.  }
7.  ?>
8.  You have been to this page <?=$count?> times.
9.  <?
10. $count++;
11. ?>
```

### 脚本 2-1 session.php 逐行解释

| 行 | 描述 |
| --- | --- |
| 2 | 启动会话或继续已有的会话。 |
| 3 | `if` 语句检查 `$count` 变量是否已设置。如果 `$count` 变量已设置，则脚本假设这是会话的延续，不采取任何操作，并继续到第 7 行。 |
| 4 | 如果 `$count` 变量未设置，则脚本假设这是一个新会话的开始，并注册变量 `$count`。 |
| 5 | 由于脚本在上一行刚刚注册了变量 `$count`，因此它使用此行为 `$count` 分配一个默认值 1。 |
| 8 | 显示一行文本，说明页面被访问的次数。 |
| 10 | 将 `$count` 变量加 1。 |

运行此脚本并多次点击刷新按钮。注意，每次你刷新页面时，页面访问次数都会增加 1。图 2-1 显示了这种示例。关闭浏览器然后在新浏览器中重新加载页面会将 `$count` 重置为 '1'，因为关闭浏览器实际上结束了会话。

### 图 2-1 session.php

![graphics/02fig01.jpg)

## 会话文件的内容

你可以通过查看 `php.ini` 文件中 `session.save_path` 设置指定的目录来查看会话变量的实际内容。在该目录下，你应该能看到一个类似于 "sess_c4a972c1745304544dc5cc1" 的文件。重要部分是文件名是以 `sess_` 开头的。之后的随机字符串是 PHP 分配给每个会话的唯一标识符。如果你在一个共享站点上或过去运行过任何会话，可能会有几个看起来像 PHP true 的文件。尝试找到时间戳与你访问示例时最接近的一个，但打开任何一个文件都会让你对会话变量是如何存储的。在文本编辑器中打开文件将显示以下内容：

```
count|i:6;
```

文件中显示的实际数字将有所不同，取决于你重新加载页面的次数。文件内容显示变量名，后面是一个管道符号 `|`，然后是变量类型标识符——在这种情况下 "i" 代表整数——最后是变量的值，后跟分号。如果你在会话中注册了多个变量，它们将按照注册的顺序列出，大多数情况下用分号分隔。例如，如果你在会话中注册了两个整数变量 `$count` 和 `$day`，它们将如下所示：

```
count|i:6;day|i:7;
```

表 2-1 详细列出了你在典型会话文件中可能会看到的常见变量类型。

### 表 2-1 会话文件中的变量类型标识符

| 符号 | 变量类型 |
| --- | --- |
| i | 整数 (Integer) |
| s | 字符串 (String) |
| b | 布尔 (Boolean) |
| d | 浮点数 (Float) |
| a | 数组 (Array) |
| O | 对象 (Object) |
| N | NULL |

## 会话期间跨页面跟踪变量

现在你已经知道如何启动会话并跟踪某些变量，如何利用这些呢？会话有无数用途，但会话真正的益处是减少你和 Web 服务器的工作量。考虑一个拥有注册用户的典型站点。该站点可能有论坛、用户可以回应的故事，以及用户可以选择启用或禁用的各种功能。

通常，你会将这些偏好存储在某些数据库中，并在用户登录站点时加载。你需要一种方法在用户查看的每个页面上记住这些值。如果用户不想在某个页面上看到投票功能，那么可以假设他们也不想在其他页面上看到它。你可以在用户每次加载页面时查询数据库以查看应该启用哪些功能，或者可以将这些信息存储在 cookie 中，但每种方法都有缺点。对于大型站点，每次加载页面都查询数据库会导致严重的服务器资源问题。

这正是会话（sessions）大显用场。你可以存储可以在多个页面访问的值。通过在会话开始时加载用户偏好，你可以将数据库查询减少到最低，并且只需要担心在用户的浏览器上存储一个 cookie，从而消除了对任何网站在浏览器上存储的 cookie 数量有限的顾虑。如果你使用 `PHP` 的会话链接重写功能，你甚至不需要担心这一个 cookie！

在接下来的示例中，你将把一些默认变量加载到会话中，就像它们来自数据库查询一样，然后将在脚本 2-3 `track_prefs2.php` 中验证会话变量是否有效。结果将显示在图 2-2 中。

#### 脚本 2-2 track_prefs1.php

```
1.  <?
2.  session_start();
3.  session_register("first");
4.  session_register("last");
5.  session_register("email");
6.  session_register("news_prefs");
7.  ?>
8.  <html>
9.  <head>
10. <title>Welcome</title>
11. <style type="text/css">
12.   p, ul, h3 {font-family: verdana, helvetica, sans-serif;}
13.   .enabled {font-weight: bold; color: green;}
14.   .disabled {font-weight: bold; color: red;}
15. </style>
16. </head>
17. <<body>
18. <?
19. function load_user_data(){
20.   global $first, $last, $email, $news_prefs;
21.   $first = "Faye";
22.   $last = "Valentine";
23.   $email = "faye@bebop.com";
24.   $news_prefs = array(
25.     "Local" => 0,
26.     "Nation" => 1,
27.     "World" => 1,
28.     "Comics" => 0,
29.     );
30. }
31. load_user_data();
32. ?>
33. <h3>Welcome</h3>
34. <p>Welcome back <b><?=$first?></b>
35. <p>Your settings have been loaded.
36. <p><a href=track_prefs2.php>View Your Settings</a>.
37. </</body>>
38. </html>
```

#### 图 2-2. track_prefs2.php

![graphics/02fig02.jpg](img/02fig02.jpg)

#### 脚本 2-2. track_prefs1.php 逐行解释

| 行号 | 说明 |
| --- | --- |
| 2 | 启动会话或继续现有的会话。 |
| 3–6 | 注册在整个会话期间使用的会话变量。 |
| 8–17 | 打印 HTML 页面的开头。 |
| 19 | 声明一个新函数 `load_user_data()`。 |
| 20 | 允许函数使用并修改脚本全局范围内的变量。这些变量对应于脚本之前注册的会话变量。 |
| 21–23 | 给会话变量分配一些字符串。 |
| 24 | 将数组赋值给会话变量 `$news_prefs`。 |
| 25–29 | 为数组分配项。 |
| 31 | 运行 `load_user_data()` 函数。 |
| 33–36 | 通知用户其设置已加载，并提供查看设置的链接。 |
| 37–38 | 关闭页面的 HTML 标签。 |

#### 脚本 2-3 track_prefs2.php

```
1.  <?
2.    session_start();
3.  ?>
4.  <<html>
5.  <head>
6.  <title>View Settings</title>
7.  <style type="text/css">
8.    p, ul, h3 {font-family: verdana, helvetica, sans-serif;}
9.    .enabled {font-weight: bold; color: green;}
10.   .disabled {font-weight: bold; color: red;}
11. </style>
12. </head>
13. <<body>
14. <h3>View Your Settings</h3>
15. <p>Hello <b><?=$first?> <?=$last?></b>,
16. <p>Email: <?=$email?>
17. <p>Your settings:<<ul>>
18. <?
19. while(list($key,$value) = each($news_prefs)) {
20.   if($value) {
21.     $value = "Enabled";
22.   } else {
23.     $value = "Disabled";
24.   }
25.   print("<li class=$value>$key: $value</li>");
26. }
27. ?>
28. </ul>
29. </body>>
30. </html>
```

#### 脚本 2-3 track_prefs2.php 逐行解释

| 行号 | 说明 |
| --- | --- |
| 2 | 启动会话或继续现有的会话。 |
| 4–13 | 打印 HTML 页面的开头。 |
| 14–17 | 欢迎用户并显示其姓名、邮箱和设置列表开头。 |
| 19–26 | 遍历 `$news_prefs` 数组。如果值为真，则将其设为“Enabled（已启用）”，否则设为“Disabled（已禁用）”。打印每个键值值。 |
| 27–30 | 关闭页面的 HTML 标签。 |

如果你一直在查看 `session.save_path` 目录下的会话文件内容，你可能会注意到那里堆积了一些文件，这取决于你打开了多少个会话示例。这些文件在用户关闭浏览器结束会话时仍然存在未被删除，是因为我们没有去销毁会话。你必须显式地销毁会话，会话文件才会被删除。之所以这样做，是因为你无法判断用户会在会话中持续多久。用户启动会话后，回家过完晚上（甚至过一个漫长的周末！），第二天回来时浏览器仍然打开在桌面上，这是完全可能的。如果用户一直在购物，由于上述原因，你肯定不想在一段固定的有限时间后删除他们的会话。

有两种方法可以应对临时目录中文件的堆积，且在大多数情况下不会对用户的会话产生不利影响。

第一种是使用 `session_destroy()` 函数：

```
session_destroy();
```

`session_destroy()` 不接受参数。`session_destroy()` 会注销与用户会话关联的所有会话变量，并删除会话创建的任何会话文件。请记住，即使变量从会话中被注销，该变量仍然存在于当前页面且其值保持不变。

接下来的脚本演示了 `session_destroy()` 函数的使用。

### 脚本 2-4 session2.php

```
1.  <?
2.  session_start();
3.  if(isset($destroy)) {
4.    session_destroy();
5.    unset($name);
6.  } else {
7.    if(!session_is_registered("name")) {
8.      session_register("name");
9.      $name = "Spike";
10.     }
11. }
12. ?>
13. <p>SESSID: <?=$PHPSESSID?>
14. <p>Name: <?=$name?>
15. <form action=session2.php method=post>
16. <input type="submit" name="reload" value="Reload Session"><br>
17. <input type="submit" name="destroy" value="Destroy Session">
18. </form>
```

### 脚本 2-4. session2.php 逐行解释

| 行 | 说明 |
| --- | --- |
| 2 | 启动会话或继续现有会话。 |
| 3–5 | 检查 `$destroy` 变量是否设置。如果设置了，说明用户点击了“Destroy”（销毁）按钮。 |
| 6–10 | 如果未设置 `$destroy`，则注册名为 `$name` 的会话变量并将该变量赋值为 "Spike"。 |
| 13–14 | 打印当前会话 ID 和 `$name` 变量的值。 |
| 15–18 | 向用户显示表单，允许其刷新当前页面或销毁与当前会话关联的会话变量。如果用户刷新页面（通过点击“Reload”或使用浏览器的刷新按钮），会话变量将重置并显示会话 ID 值。如果用户点击“Destroy”按钮，则与页面相关的会话文件将被删除，从而删除会话变量的值。 |

在点击“Reload Session”和“Destroy Session”按钮时，注意你临时目录中的文件。每次你点击“Destroy Session”，注意具有相应会话 ID 的会话文件会从你的 `session.save_path` 目录中删除。每次点击“Reload Session”都会在该目录中重新创建文件。

管理孤立会话文件的另一种方法是利用 PHP 对这些会话文件的自动“垃圾”清理。用文本编辑器打开你的 `php.ini` 文件并滚动到 `[session]` 设置。查找以下两个设置：

```
; 每次会话初始化时启动“垃圾回收”过程的百分比概率。
session.gc_probability = 1
; 在此秒数之后，存储的数据将被视为“垃圾”，并由垃圾回收过程
; 进行清理。
session.gc_maxlifetime = 1440
```

第一个设置 `session.gc_probability` 设置了被识别为垃圾文件的删除百分比概率。默认值“1”意味着每次启动会话时有 1% 的概率。

第二个设置 `session.gc_maxlifetime` 设置了会话在标记为垃圾之前可以存在的寿命（秒为单位）。默认值“1440”意味着超过 24 分钟的每个会话都被视为垃圾。
