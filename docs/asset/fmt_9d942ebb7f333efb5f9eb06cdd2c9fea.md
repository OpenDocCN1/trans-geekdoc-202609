
你会知道 `$answer_id[$i]` 包含主键，而 `$answer_text[$i]` 是该行的答案。
之前的代码部分只会在有答案的地方打印表单元素。你应该为管理员提供输入新答案的区块。

```php

while ($account < 10) {

  $account++;

  print text_field("answer_text[$account]",","60);

  print hidden_field("answer_id[$account]",0);

  print "<br>\n";

}

```

这将完成表单，提供你需要空白元素。对于这些空白答案，表单将包含以下内容：

```html

<input type="text" name="answer_text[8]" value="" size="60" 

<input type="hidden" name="answer_id[8]" value="0"><br>

```

## 第 9 章：调查调查 241

在这些表单元素中，隐藏字段的值被设置为 0。这样一来，当轮到处理这些表单元素时，脚本将有内容可以进行评估：如果 `$Answer_id[$i]` 等于 0 或为空 (`$Answer_id[$i]`)，则表示这是一个新元素。

当表单提交时，这段代码将运行。
将会有 10 个元素需要循环，因此使用 `for` 循环非常好用。

```php

for ($i = 1; $i <= 10; $i++)

{

  if (!empty($answer_text[$i]))

```

首先，我们确保有可用的答案。

```php

{

  $answer = cleanup_text($answer_text[$i]);

  if (empty($answer_id[$i]))

    $query = "insert into answers

      (question_id, answer)

      values

      ($question_id, 'answer')

    ";

}

```

如果 `$answer_id` 元素不为空（意味着它不等于 0），则执行插入语句。

```php

else

{

  $query = "update answers

    set question_id = $question_id

      answer = '$answer'

    where answer_id = ".$answer_id[$i]"

  ";

  safe_query($query);

}

```

否则，如果存在现有答案，一个更新查询将解决问题。

## admin_get_winner.php

该文件的大部分内容是可以读的。你的目标是从数据库中随机抽取一个合格的获者。首先，你使用 `weekstart` 函数（在本章之前的“Functions and code from /book/survey/header.php”部分讨论）来获取本周开始的日期。

```php

$qweekdt = weekstart($weekdate);

list($thisweek) = mysql_fetch_array(safe_query("select $qweekdt"));

print subtitle("Draw a winner for the week of $thisweek");

```

然后，你创建一个符合条件的查询。如你所见，我们决定除了在上周登录外，你还需要输入姓名、电子邮件地址以及一个合法的年龄。

```php

$query = "select name, email, user_id from users

where (create_dt) = week('$thisweek')

and year(create_dt) = year('$thisweek')

and name is not null and name != ''

and email is not null and email != '' and email like

'%%%%'

and age > 0

and country is not null and country != '";

$result = safe_query($query);

$tot = mysql_num_rows($result);

```

在获得合格参赛者的总数后，脚本将做出几个决定来确定获者。首先，它需要考虑没有可能获者的情况。

```php

if($tot ==0)

{

  echo "There were no entrants this week";

}

```

我们已经运行了一个获取潜在获者的查询。结果集中的第一行是行号 0。如果只有一个可能的获者，行 0 就是唯一返回的行。

```php

else

{

  if($tot == 1)

{

    // 如果只有一个参赛者，他们就赢了。

```

## 第 9 章：调查

```php

$winner = 0;

```

然而，如果存在多种可能性，则会为随机数生成器设置种子，并提取出一行。注意，总行数将大于最终行号（因为第一行编号为 0）。这就是为什么随机数的顶部范围必须是 `Stot-1`。

```php

else

  $mt_rand((double)microtime()*1000000);

  $winner = mt_rand(0,$stot-1);

```

```php

mysql_data_seek($result, $winner);

list($name, $email, $user_id) = mysql_fetch_array($result);

$urlthisweek = urlencode($thisweek)

print paragraph(

  "<b>$name</b> $email"

  "<b><font color=red>WINNER!</font></b>"

  anchor_tag("admin_winners.php?weekdate=$urlthisweek",

  "&notify&user_id=$user_id",

  "Notify Winner"

);

```

这段代码获取了关于获者的所需的信息，并提供指向 `admin_winners.php` 页面的链接，该页面包含了正确的 `user_id`、与此奖项相关的周，以及变量 `$what`，该变量将标识我们想要运行的 `admin_winners.php` 部分。
该文件还有更多内容，但你应该能够遵循代码中包含的注释。

## admin_winners.php

我们创建了几个页面以确保获者收到这个令人兴奋的消息，并以一种提供某种安全性的方式发出通知。这虽然不多，但为了合理地确保声领奖品的人就是你想要的人，你需要使用登录系统，而一个无聊小调查的用户可能对跟踪另一个奖励并不感兴趣。
我们在这里能做的最好就是确保如果一个不当的人在某周看到了领奖信息，他们他们在未来的几周内也无法伪造我们的系统系统。当我们发送获者通知时，我们将包含一个八字符的领奖代码。此奖项只有知道该代码才能领取。

## 第三部分：简单应用程序

为了确保获者收到这个令人兴奋的消息，并以一种提供某种安全性的方式发出通知。这虽然不多，但为了合理地确保声领奖品的人就是你想要的人，你需要使用登录系统，而一个无聊小调查的用户可能对跟踪另一个奖励并不感兴趣。
我们在这里能做的最好就是确保如果一个不当的人在某周看到了领奖信息，他们他们在未来的几周内也无法伪造我们的系统。当我们发送获者通知时，我们将包含一个八字符的领奖代码。此奖项只有知道该代码才能领取。

为了确保获者收到这个令人兴奋的消息，并以一种提供某种安全性的方式发出通知。这虽然不多，但为了合理地确保声领奖品的人就是你想要的人，你需要使用登录系统，而一个无聊小调查的用户可能对跟踪另一个奖励并不感兴趣。
我们在这里能做的最好就是确保如果一个不当的人在某周看到了领奖信息，他们他们在未来的几周内也无法伪造我们的系统。当我们发送获者通知时，我们将包含一个八字符的领奖代码。此奖项只有知道该代码才能领取。

为了尽可能确保安全，我们希望该代码是唯一的且难以猜测的。

```php

mt_rand((double)microtime()) * 1000000;

$claim_code = substr(uniqid(),8);

```

使用 `uniqid()` 和 `md5()` 函数来创建一个 32 字符的字符串，`substr()` 将其限制为 8 字符。

```php

$query = "insert into answers

(date, user_id, claim_code)

values

(now(), $user_id, '$claim_code')";

```

当表单提交时，这段代码将执行。

```php

if (!empty($answer_text)) {

  $answer = cleanup_text($answer_text[$i]);

  if (empty($answer_id[$i]))

    $query = "insert into answers

      (question_id, answer)

      values

      ($question_id, 'answer')

    ";

}

```

当表单提交时，这段代码将执行。

（注：此处由于原文中存在部分逻辑重复。）

为了尽可能确保安全，我们希望该代码是唯一的且难以猜测的。

使用 `uniqid()` 和 `md5()` 函数来创建一个 32 字符的字符串，`substr()` 将其限制为 8 字符。

```php

mt_rand((double)microtime()) * 1000000;

$claim_code = substr(uniqid(),8);

```

当表单提交时，这段代码将执行。

```php

if (!empty($answer_text)) {

  $answer = cleanup_text($answer_text[$i]);

  if (empty($answer_id[$i]))

    $query = "insert into answers

      (question_id, answer)

      values

      ($question_id, 'answer')

    ";

}

```

（注：由于提供的原文中存在大量段落重复和逻辑混乱，翻译已根据原文提供的结构进行了对应处理，保留了所有 Markdown 标记。）

## 第 10 章

## 目录

本章内容

- 使用面向对象的代码工作
- 查看数据库架构
- 规避 MySQL 的局限性
- 在 PHP 内部运行 shell 命令

在本章中，我们将向如何一种创建在线目录的方法。你将看到如何展示和管理一个展示某些典型零售商品的应用程序。

我们，作为这本书的作者，认为你是一个明智的人，而且在技术文献方面具有极佳的品味。我们还相信，你选择这本书是因为你想尽可能地学习关于使用 PHP 和 MySQL 进行应用程序开发的知识。因此，我们不会浪费任何时间。每一章都会引入额外的挑战，或者至少呈现一些新颖且不同的内容。本章也无例外。

如果本章使用第 9 章调查应用程序中提供的函数，那么就没有什么新材料可以展示了。整个应用程序只需要简单的数据库架构、几个带有连接（joins）的查询，以及对 `/functions/` 文件夹中 HTML 函数的调用。

为了保持趣味性，该应用程序使用了完全不同的代码组织方式。这个调查利用了面向对象（或简称 OO）的。然而，我们并没有放弃所有这些函数。其中一些实在太方便了（比如 `safe_query()`）。

![](img/245156cc770929860a3ede93c01f9981_277_0.png)

> 第 7 章涵盖了与面向对象编程相关的概念和术语。在本章中，我们假设你已经阅读并理解了这些信息。

## 确定应用程序的范围和目标

我们对这个应用程序的目标相当适度。想象一下，你拥有某种零售店，里面有你想要推销的商品。此外，假设你对实际上在 Web 上进行交易并不感兴趣。也许你只是对这种处理信用卡的新奇方法感到疑虑。或者，你正在运行一个复杂的逃税计划，这要求你只处理无标记的美元大钞。

![](img/245156cc770929860a3ede93c01f9981_278_0.png)

此目录中使用的代码将重用在购物车应用程序中，在那里我们将展示如何处理信用卡交易。
