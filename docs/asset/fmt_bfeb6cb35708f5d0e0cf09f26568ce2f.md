
## 列表 46-2（继续）

```php
$page_string = <<<EOT
$top_matter_string
```

```html
<H2></CENTER>
<TABLE ORDER=2>
<TR>
<TD VALIGN=TOP WIDTH=40%>$left_side</TD>
<TD VALIGN=TOP WIDTH=60%>$right_side</TD>
</TR>
</BODY></HTML>
EDIT:
{
    return($page_string);
}
function highScore () {
    // 处理数据库更新，当玩家
    // 获得高分并提交了
    // 姓名用于记录时
    if ($this->highScorePosted) {
        $this->highScorePosted = TRUE;
        if (get_post_value('NICKNAME') &&
            get_post_value('ANSWER_COUNT') &&
            get_post_value('CREDIT') &&
            get_post_value('CHECKSUM') &&
            $this->checksumValid) {
                get_post_value('ANSWER_COUNT');
                get_post_value('CREDIT');
                get_post_value('CHECKSUM');
            }
        $name = get_post_value('NICKNAME');
        $answer_count = get_post_value('ANSWER_COUNT');
        $credit = get_post_value('CREDIT');
        $query = "insert into high_scores\n            (name, answer_count, credit)\n            values\n
            ('$name', '$answer_count', $credit)";
        $connection =
            $this->game->game->getDbConnection();
        $result = mysql_query($query, $connection);
    } else {
        // 什么都不做 - 添加高分失败
        // 不应该是致命性错误
    }
}
私有函数
private function makeTopMatter($title) {
    // 返回用于普通页面和
    // 错误页面的头部，包含
    // HTML head 和标题
```

```php
$return_string = <<EOT
<HTML><HEAD><TITLE>$title</TITLE></HEAD>
<BODY BODYCOLOR=#FFFFFF><CENTER>
<h1>$title-</h1>
<FONT SIZE=-1 COLOR=BLUE>
(你有多大<B>确定</B>？)</FONT>
</H1></CENTER>
EOT;
return($return_string);
}
private function _currentQuestionString () {
global $PHP_SELF;
return("<H2>
$this->_y_game->getCurrentQuestion())
<FORM METHOD=POST ACTION=\$PHP_SELF HIDDEN\">
<INPUT TYPE=CHECKBOX NAME=postcheck=1\">
$this->_y_game->getCurrentQuestion())
</FORM>"
}
```

```php
private function _distractorString($question) {
// 创建用于展示单选按钮选项
// 选项的实际 HTML。
// 假设代表实际选项的数组
// 已经提前计算好，可以通过
// getDistractorArray() 从问题
$distractor_array = $question->getDistractorArray();
$distractor_string = "<TR ALIGN=TOP><TD>:
$distractor_string .= "\n<TABLE ORDER=1 BCOLOR=#AAAFCI><TR><TH>
<TH>至少大于</TH>:
$count = 1; // 优先使用从 1 开始的标签，
// 这样我们可以直接用 if ($label)
$total = count($distractor_array);
foreach ($distractor_array as $distractor) {
$lower_selected = ($count == 1) ?
"CHECKED" : "";
$upper_selected = ($count == $total) ?
"CHECKED" : "";
$formatted_distractor =
($distractor > 10000) ?
number_format($distractor) : $distractor;
$distractor_string .= "<TR><td><INPUT TYPE=RADIO NAME=\"lower
VALUE=$count
$lower_selected </TD>\n";
$count++;
}
$distractor_string .= "\n";
```

```html
<TD><INPUT TYPE=RADIO NAME=\"upper
VALUE=$count
$upper_selected </TD></TR>;
}
$distractor_string = "</TABLE>";
$distractor_string = "</TD>";
$distractor_string = "
<INPUT NAME=\"Submit guess! VALUE=\"Submit guess\"
TYPE=SUBMIT\">
$distractor_string = "</TD></TR></TABLE>";
}
```

```php
private function _previousQuestionString() {
if (!$this->_game->getPreviousQuestion()) {
$return_string = "";
} else {
$return_string = $this->_game->getPreviousQuestion() ?
$this->_rightString() :
$this->_wrongString();
}
return($return_string);
}
```

```php
function rightString() {
return("<H2><FONT COLOR=GREEN>正确!</FONT></H2>");
}
```

```php
function wrongString() {
return("<H2><FONT COLOR=RED>错误!</FONT></H2>");
}
```

```php
private function highScoreEligible() {
// 获取游戏结束的分数，并查询
// 数据库以查看玩家是否符合
// 高分列表条件
$query = "select name, answer_count, credit
from high_scores
order by answer_count desc, credit desc
limit 10";
$connection =
$this->_game->getDbConnection();
if ($connection && is_resource($connection)) {
$result = mysql_query($query, $connection);
$eligible = false;
```

```php
if (mysql_num_rows($result) > 9) {
    while ($row = mysql_fetch_assoc($result)) {
        $answer_count = $row['answer_count'];
        $credit = $row['credit'];
        if (($this->_game->getCorrectAnswers() ==
            $answer_count) &&
            ($this->_game->getCredit())) {
            $eligible = TRUE;
            break;
        }
    }
} else {
    $eligible = TRUE;
}
if (!$eligible) {
    throw new Exception("Game display database connection");
}
// 校验和在提交分数时计算
//（由正确答案数量加
// 积分组成），以防止
// 伪造（除非校验方案
// 发表在书籍或其他别处）。
private function checksum($answer_count, $credit) {
    return ($checksum = $this->_makeChecksum($answer_count, $credit));
}
private function makeChecksum($answer_count, $credit) {
    return (round($answer_count)) *
}
private function highScoreString() {
    // 用于向高分列表提交
    // 用户名的欢迎语及 HTML 表单
global $PHP_SELF;
    $answer_count = $this->_game->getCorrectAnswers();
    $credit = $this->_game->getCredit();
    $checksum = $this->_makeChecksum($answer_count, $credit);
    $result_string =
```

```html
<H2>恭喜！你获得了高分</H2>.
- 输入你的姓名（或昵称）用于
- 分数：
-<form method="post" action="$PHP_SELF">
<input name="NICKNAME" type="text" size="30">
<input name="ANSWER_COUNT" type="hidden" value="$answer_count">
<input name="CREDIT" type="hidden" value="$credit">
<input name="CHECKSUM" type="hidden" value="$checksum">
<input name="Submit" type="submit" value="Submit">
<input type="checkbox" value="1">
<input type="hidden" name="HIGHSCORE" value="1">
</form>
```

```php
"<TR>$rank</TH><td>$name</TD>"
"<TD>$answer_count</TD><td>$credit</TD></TR>";
$rank++;
$result_string .= "<TABLE>";
return($result_string);
} else {
    throw new Exception("Game display has no database connection");
}
private function gameGameStateString() {
    // The HTML table
    $correct_answers = $this->game->getCorrectAnswers();
    $credit = round_to_digits($this->game->getCredit(), 2);
    $level = $this->game->getLevel();
    return("<TABLE CELLPADDING='ID'>
<TR BCOLOR='$this->blueColor'>
<TH>Total correct answers:</TH>
<TD>$correct_answers/$this->redColor</TD></TR>
<TR BCOLOR='$this->redColor'>
<TH>Credit remaining:</TH>
<TD>$credit</TD></TR>
<TR BCOLOR='$this->blueColor'>
<TH>You have reached level:</TH>
<TD>$level</TD></TR></TABLE>");
}
?>
```

注意，在 `GameDisplay` 类中，我们使用了 PHP5 中引入的面向对象结构。构造函数名是 `__construct()`，而不是与类名同名。我们将不供外部使用的函数指定为 `private`（私有），这可以防止其他类调用它们。

该类的大多数私有函数涉及查询 `Game` 对象以获取其封装在 HTML 中的信息。这类函数中最有趣的函数之一是 `distractor_string()`，它创建了答案选项的实际显示。这里的工作范围如下：

- 答案的上下限在数据库中指定，还包括应该显示多少个选项以及它们如何进行缩放。
- `Question` 对象接收这些信息，并在构造答案时控制其的所有中间步骤。
- `GameDisplay` 对象查询 `game` 获取当前问题，然后查询 `question` 以发现上下限和中间步骤。然后，它将这些值封装在 HTML 中，以单选按钮选项的形式呈现，并预选中最大的答案范围。

## 案例研究

### game_text_class.php

我们这些谦虚的作者确实为了让这些内容变得有趣而努力了，但在情况下，我们必须承认失败。`GameText` 类只是将一些模板化的 HTML 封装在成员函数中，以便 `GameDisplay` 类可以请求。说够了吗？

这些函数使用了我们最喜欢的创建大块模板代码的技术，即 `heredoc` 语法。（有关 `heredoc` 用法的更多信息请参见第 8 章）。列表 46-3 显示了 `game_text_class.php`。

### 列表 46-3: game_text_class.php

```php
<?php
class GameText
{
    function __construct () {
        // no vars, nothing for constructor to do
    }
    function Introduction () {
        $intro = <<EOT
        <h2>欢迎来到确定性测验！</h2>
        这个游戏测试的是
        <li>你对“有多少”的了解程度</li>
        <li>你对
        “关于你知道有多少”的
        了解程度！
        <h4>目标是尽可能准确地回答问题。</h4>
        回答问题
        （从左侧的题目开始），通过选择
        你认为正确答案所在上方和下方的数值。
        如果范围内包含了真实答案，则答案是正确的。
        你的猜测越精确，你的生存时间就越长。
        共有十个等级；如果你觉得题目
        太简单，请继续下去。
        EOT;
        return($intro);
    }
    function rules () {
        $rules = <<EOT
        <h4>每个错误答案从你的积分中扣除四分。</h4>
        <<li>每个正确答案增加一分积分，但要减去你答案范围的惩罚。指定
        整个范围将扣除四 分（总计 -3 分）；
        指定范围的单个步骤则不扣分
        （总计 +1 分）。中间范围将产生中间结果。
EOT;
```

```php
<li>积分上限为 15 分。
<li>每当你的积分低于零时，游戏结束。
EOT;
return($rules);
}
```

```php
function gameLostText () {
    global $PHP_SELF;
    $game_over = <<EOT
<h1>感谢参与！</h1>
感谢参加确定性测验，并且是一个
```
