

### 可能出错？

可能出现三种常见问题。首先，如前所述，在比较时应始终使用三重等号（===）而非双重等号（==）。三重等号确保比较项的值和类型相同。这一点很重要，因为你可以从 strpos() 中得到 0 作为有效位置，以及从 strstr() 和 strrpos() 中得到空字符串作为有效返回值，而这两者用 == 都会匹配 False。

其次，这些函数区分大小写。在上述示例中，使用 strstr($string, 'Approved') 将返回 False。strpos()、strrpos() 和 strstr() 的不区分大小写版本分别是 stripos()、strripos() 和 stristr()。

最后，请记住，此处检查的是非常简单的子字符串，而非单词。如果你需要做一些花哨的事情，例如查找以 *批准词根* 开头的单词，包括 *批准* 和 *已批准* 但不包括 *不批准*，则需要更强大的工具：正则表达式。我们将在第 69 页的 “#39：正则表达式” 中介绍如何使用它们。

## #37：替换子字符串

使用 str_replace() 函数执行简单的字符串替换。以下是如何从卡通字符串中将 *兔子* 替换为 *鸭子*：

```php
$string = "It's wabbit season!";
print(str_replace("wabbit", "duck", $string));
```

请注意，str_replace() 不会替换原始字符串中的子字符串。如果要这样做，请将其重新分配给原始字符串：

```php
$string = str_replace("wabbit", "duck", $string);
```

str_replace() 还有几个额外功能。要仅替换子字符串的前 n 次出现，请将数字作为第四个参数添加（这对于仅替换第一次出现尤其有用）：

```php
str_replace("wabbit", "duck", $string, n);
```

要删除子字符串的所有出现，只需将空字符串作为替换参数：

```php
$string = str_replace("wabbit", "", $string);
```

你可以通过将多个子字符串放入数组来指示 str_replace() 替换它们：

```php
$ugly_words = array("hamburger", "bacon", "bucket o'grease");
$string = str_replace($ugly_words, "Atkins-friendly foods", $string);
```

此示例将 $string 中的所有 hamburger、bacon 和 bucket o'grease 替换为 Atkins-friendly foods。

你甚至可以提供两个大小相同的数组作为查找和替换参数，str_replace() 将用搜索数组中与替换数组相同索引的项进行替换：

```php
$ugly_words = array("hamburger", "bacon", "bucket o'grease");
$replacements = array("carrot", "broccoli", "2% milk");
$string = str_replace($ugly_words, $replacements, $string);
```

这将把所有 hamburger 替换为 carrot，所有 bacon 替换为 broccoli，所有 bucket o'grease 替换为 2% milk。

### 可能出错？

str_replace() 的一个问题是，它会替换与你给出的模式匹配的所有内容，无论它在字符串中的什么位置。如果你将 off 替换为 on，你会发现你的 officials 变成了 onicials，你的 coffins 变成了 conins。

因此，虽然 str_replace() 对于从小规模字符串中删除不需要的单词非常有价值，但对于更复杂的任务，你需要正则表达式。（参见第 69 页的 “#39：正则表达式”。）

## #38：使用 pspell 查找并修正拼写错误的单词

任何使用过 Google 的人都在搜索中拼错过单词，例如 alternative music。而 Google 始终会乐意地返回 “Did you mean alternative music?”

如果你的网站有搜索功能，在未找到结果（或结果不足）时能够建议拼写错误的单词，这是一个非常有用的功能，尤其是因为客户的拼写能力不足可能会让你失去一笔交易。幸运的是，有一个名为 pspell 的 PHP 模块，它允许你检查单词的拼写，并从 pspell 的默认词典中建议替换词。如果你愿意，甚至可以创建自定义词典。不过，首先你需要确保已安装 pspell 扩展库。请尝试这个测试脚本：

```php
<?php
$dict_config = pspell_config_create('en', 'american');
?>
```

如果出错，说明你没有安装 pspell 扩展库。请翻回到第 27 页的 “#18：为 PHP 添加扩展” 查看如何操作。

### 使用默认词典

下面是一个帮助你开始使用 pspell 的小函数：

```php
<?php
function suggest_spelling($string) {
    // Suggest words for misspelled strings.
    $dict_config = pspell_config_create('en', 'american');
    pspell_config_ignore($dict_config, 3);
    pspell_config_mode($dict_config, PSPELL_FAST);
    $dictionary = pspell_new_config($dict_config);

    // Make sure we know whether we've suggested anything.
    $suggested_replacement = false;

    // Now we've got it set up, break it up by words.
    $string = explode(' ', $string);
    foreach ($string as $key=>$value) {
        $value = trim(str_replace('.', '', $value));
        if ((strlen($value) > 3) && (! pspell_check($dictionary, $value))) {
            // If we can't find a suggestion
            $suggestion = pspell_suggest($dictionary, $value);
            // Suggestions are case sensitive, so check first
            if (strtolower($suggestion[0]) != strtolower($value)) {
                $string[$key] = $suggestion[0];
                $suggested_replacement = true;
            }
        }
    }

    if ($suggested_replacement) {
        // We had a suggestion, so return the data.
        return implode(' ', $string);
    } else {
        return null;
    }
}
?>
```

要使用此函数，请使用字符串参数调用 suggest_spelling()，如本示例所示：

```php
<?php
// Searchstring is taken from the previous form.
$searchstring = $_POST['customer_input'];

$spell_suggest = suggest_spelling($searchstring);
if ($spell_suggest) {
    // pspell found a suggestion.
    echo "Did you mean <i>$spell_suggest</i>?";
}
?>
```

要初始化 pspell，必须配置一个词典。为此，你需要创建一个指向词典配置文件的句柄，修改该句柄上的几个设置，然后使用词典配置创建指向实际词典的第二个句柄。

如果这听起来有点复杂，请别担心。代码很少更改，因此你通常可以直接从其他脚本复制。不过，让我们逐块看一下。以下是配置词典的代码：

```php
$dict_config = pspell_config_create('en', 'american');
pspell_config_ignore($dict_config, 3);
pspell_config_mode($dict_config, PSPELL_FAST);
```

$dict_config 是控制词典设置的初始句柄。你必须将所有设置加载到 $dict_config 中，然后使用它创建词典。在此示例中，pspell_config_create() 创建一个使用美国拼写的英语（en）词典。

pspell_config_ignore() 将词典设置为忽略所有三个字母及以下的单词。这样做是因为检查每个 a 和 the 会很耗时。

最后，pspell_config_mode() 告诉 pspell 你希望如何查找。你有三种选择：

- PSPELL_FAST 是一种快速方法，返回尽可能少的建议拼写。
- PSPELL_NORMAL 以正常速度返回中等数量的拼写。
- PSPELL_SLOW 检查需要一些时间，但返回尽可能多的建议。

我们可以在此处使用其他配置（例如添加自定义词典，我稍后会介绍），但由于这是一个快速而粗糙的拼写检查，我们将使用这一行仅创建词典本身：

```php
$dictionary = pspell_new_config($dict_config);
```

此时，使用词典有两种基本方法：

- 1. pspell_check($dictionary, word) 如果 word 在词典中，则返回 True。
- 2. pspell_suggest($dictionary, word) 如果 word 不在词典中，则返回建议单词的数组，数组中的第一个条目是最可能的候选项。如果单词在词典中，或没有建议，则此函数不返回任何内容。返回的单词数量因情况而异，但使用 PSPELL_SLOW 时会更多，使用 PSPELL_FAST 时会更少。

> **注意** 这些函数不检查上下文拼写。即使你本意是 Mary had a little lamb，Mary hat a ladle lam 也能完美通过检查。此外，如果单词长度低于 pspell_config_ignore() 设置的字符串长度，pspell 始终返回 True，因此在这种情况下，像 jlz 这样小巧但明显拼写错误的单词仍会返回 True。

