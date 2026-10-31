
```
if (mysql_result($result,0) > 0)
{
    print "<h2>sorry - your domain has been blocked from this page</h2>\n";
    exit;
}
```

上述代码包含在处理应用程序核心之前你需要的信息。这些 include 很清楚。出于谨慎考虑，这些 include 被放在了一个 if 语句中。一旦头部已被加载，就无需再次重新加载。我们可以通过创建一个名为 LOADED_HEADER 的常量来确保这种情况不会发生。如果偶然此页面被第二次加载，你也不必担心 include 会被导入多次。

![](img/de0823012275cf4ceebdb822a56e6b71_266_0.png)

> 请记住 PHP 4 具有 include_once 构造，它可确保文件不会被多次包含。

如前所述，这里有一个阻止域名的功能，该应用程序将使用 $REMOTE_HOST 变量来实现。这几乎没有必要，而且很容易注释掉这段代码。为了理解这段代码，请更仔细地查看查询，特别是 like 谓词。当我从我的 ISP（att.net）拨号上网时，我的 REMOTE_HOST 类似于这样：119.san-francisco-18-19rs.ca.dial-access.att.net。当你阻止域名时，你将在顶级域名上进行操作——在本例中为 att.net。而这个顶级域名将存储在数据库中。因此查询将在顶级域名名称之前检查任意数量的通配符字符。

要实现这一点，你需要将域名与 % 通配符字符连接起来。例如，查询将针对 %att.net 进行操作。这可能与你典型的 like 谓词有些不同。这是使用 SQL 的另一种强大技术。

还请注意，select 语句的开头不包含 select count(*)，而是选择了 select 1。这是一个测试是否有任何行满足 where 子句条件的好方法。如果 where 子句匹配任意数量的行，查询将返回一个值为 1 的单列，在编程世界中这意味着 TRUE。如果没有返回任何行，你就知道查询的 where 部分没有匹配项。

## WEEKSTART()
这个函数创建一个 MySQL 函数来获取一周开始的日期。你在应用程序中使用它来为当前周挑选获胜者。

```
function weekstart ($when="")
{
    if (empty($when)) { $when = "now()"; }
    elseif ($when != "create_dt") { $when = "'$when'"; }
    return "from_days(to_days($when)-dayofweek($when) + 1)";
}
```

其工作原理如下：MySQL 的 to_days() 函数返回自公元 1 年 1 月 1 日以来的天数整数。dayofweek() 返回一个表示一周中某天的整数（星期日等于 1，星期六等于 7）。因此，(to_days($now)-dayofweek($when) + 1) 部分将返回一个表示所讨论周的星期日的整数。from_days() 函数随后将该数字转换为日期。以下是于 2000 年 7 月 27 日星期四（本章撰写之日）运行此查询的结果：

```
mysql> select from_days(to_days(now())-dayofweek(now()) + 1);
```

| from_days(to_days(now())-dayofweek(now()) + 1) |
|---|
| 2000-07-23 |

1 行在集合中 (0.00 秒)

请注意，这里传递的值可以是一个表示日期的字符串，可以为空，或者可以是 users 表中的一个字段——即 create_dt 字段。

## COUNTRYLIST()
这个函数创建一个国家名称的下拉列表。

```
function country_list ()
{
    $countries[""] = "";
    $countries = array_merge($countries
        ,db_values_array("countries","country")
    );
    return $countries;
}
```

使用 db_values_array() 函数（在本章前面“可重用函数”部分讨论过）来获取国家及其缩写的数组。

## STATE_LIST()
这会创建一个州名称的下拉列表。

```
function state_list ()
{
    $states[""] = "";
    $states = array_merge($states
        ,db_values_array("states","state","statename","state")
    );
    return $states;
}
```

使用 db_values_array() 函数（在本章前面“可重用函数”部分讨论过）来获取国家及其缩写的数组。

## FETCH_QUESTION()
这个函数抓取 questions 表中一行的内容并将列分配给全局变量。

```
function fetch_question ($question_id="")
{
    if (empty($question_id)) { $question_id = 0; }
    $result = fetch_record("questions","question_id",$question_id);
    return $result;
}
```

这将运行 fetch_record() 函数并根据 questionid 从数据库返回有关特定问题的所有信息。

## FETCH_USER()
这个函数抓取 users 表中一行的内容并将列分配给全局变量。

```
function fetch_user ($user_id="")
{
    if (empty($user_id)) { $user_id = 0; }
    $result = fetch_record("users","user_id",$user_id);
    return $result;
}
```

根据 user_id 返回结果集。

## Interesting Code Flow
有几个页面在这个应用程序中值得一些解释。然而，如果你理解上一节中的函数，你应该能够跟上其中的大部分。

## admin_question.php
这是一个相当冗长的页面，有充分的理由：它用于在数据库中添加、编辑和删除问题。页面中将被运行的部分将由表单或链接传递的值决定。第一次运行时不会传递任何变量，因此将显示当前问题的列表以及用于输入新问题的表单。数据库中已存在问题的每个链接看起来都像这样：

```
<a href="admin_questions.php?what=edit&question_id=2" >
```

当点击这样的链接，并且 admin_questions.php 脚本再次运行时，脚本的最后部分将被运行，如下所示：

```
else
{
    $qform_title = "Edit A Question : $question_id";
    fetch_question($question_id);
}

print subtitle($qform_title);

print start_form("admin_questions.php");

print paragraph("<b>Question:</b>",
text_field("question",$question,60));
```

注意你如何通过一次函数调用（fetch_question()）获取与 $question_id 关联的所有信息。由于函数的创建方式，这会自动为你提供 $question 的全局变量。

接下来，进入这个循环：

```
$acount = 0;
if ($question_id > 0)
{
    $result = safe_query("select answer_id, answer
        from answers
        where question_id=$question_id
        order by answer_id
    ");
    while (list($aid,$atxt) = mysql_fetch_array($result))
    {
        $acount++;
        print text_field("answer_text[$acount]","$atxt",60);
        print hidden_field("answer_id[$acount]","$aid");
        print " ($aid)<br>\n";
    }
}
```

这里的数字 10 将每个问题的答案数量限制为 10。此块获取所选问题的答案并在文本字段中打印出来。附加信息放在隐藏字段中。当打印出来时，一个答案的结果将如下所示：

```
<input type="text" name="answer_text[1]" value="Answer"
size="60" >
<input type="hidden" name="answer_id[1]" value="10">
```

当提交此表单时，$answer_text 将是一个数组。$acount 将看到数组的键对每个额外的表单字段递增 1。请注意，我们在这里需要使用隐藏的表单元素。这是因为每个答案需要三条信息：答案编号是多少（1-10）、答案文本，以及如果答案来自数据库，我们需要知道答案来自的行主键。隐藏字段将创建一个名为 $answer_id 的数组。该数组中每个元素的值将是存储答案的行主键。该数组的索引将与 $answer_text 的索引相匹配。所以在代码中看起来像这样，

```
$i = 1;
$answer_text[$i];
$answer_id[$i];
```

你会知道 $answer_id[$i] 包含一行主键，而 $answer_text[$i] 是属于该行的答案文本。

前一段代码只会在有答案的地方打印出表单元素。但你应该提供空白表单元素，以便管理员可以输入新答案。

```
while ($acount < 10)
{
    $acount++;
    print text_field("answer_text[$acount]","",60);
    print hidden_field("answer_id[$acount]",0);
    print "<br>\n";
}
```

这将完成表单，提供你所需的所有空白元素。对于这些空白答案，表单将包含以下内容：

```
<input type="text" name="answer_text[8]" value="" size="60" >
<input type="hidden" name="answer_id[8]" value="0"><br>
```
