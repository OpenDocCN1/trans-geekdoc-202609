
但我们也想偷懒：

`$_simple` 是让我们能够采用简化编码风格的关键——它是一组要分配给无标签值的属性名称列表。此处，将其设置为 `array('src')` 表示，如果我们只接收到一个普通字符串作为参数，则该字符串即为 img 标签 src 属性的值。

来看看这里调用的函数。

首先是 `parse_arguments()` 函数。我们向它传递三个参数：一个包含传入 `image_tag()` 的参数的数组，以及两个静态数组。你可能会注意到，尽管参数被声明为传入变量的引用，但我们仍然可以为它们初始化默认值。这是新 PHP 引擎版本中一个非常有用的功能。能够定义默认值意味着调用者可以忽略不适用的参数。

在函数内部，我们使用强制类型转换运算符来确保这些参数是数组，并设置一些变量，用于在遍历参数时保存值（请注意，在 PHP 5 中，你可以为按引用传递的参数分配默认值；这大大简化了函数的调用）：

```
function parse_arguments($args=array(), &$simple=array(), &$defaults=array())
{
    $args = (array)$args;
    $simple = (array)$simple;
    $defaults = (array)$defaults;
    $key = NULL;
    $result = $defaults;
    $result['_defaults'] = $defaults;
    $result['_simple'] = $simple;
```

我们将 `$result` 变量（即函数最终将返回的内容）初始化为 `$defaults` 的副本。这样可以确保 `$defaults` 数组中定义的所有内容都会作为标签的属性返回。然后，我们将这些数组本身放入 `$result` 中，以便它们可以被传入原始函数的参数修改或替换。这样，我们就可以在页面代码中更改默认值和简单值（例如设置默认图像大小或边框宽度），而无需重写函数本身。

接下来，我们将遍历参数列表。关联数组会合并到 `$result` 中，空参数会被忽略，而其他参数将被分配给来自 `$_simple` 数组的命名参数：

```
$i = 0;
$sc = count($simple);
foreach ($args as $arg)
{
    if ($arg == NULL || (is_array($arg) && count($arg) == 0))
    {
        // do nothing
    }
    elseif (is_object($arg))
    {
        $result = array_merge($result, get_object_vars($arg));
    }
    elseif (is_assoc($arg))
    {
        $result = array_merge($result, $arg);
    }
    else
    {
        if ($i < $sc)
        {
            $key = $simple[$i++];
            if (empty($arg) || !isset($result[$key]))
            {
                $result[$key] = $arg;
            }
        }
        else
        {
            if ($key == NULL)
            {
                user_error("Argument '$arg' was passed with no
                available target - aborting...\n", E_USER_ERROR);
            }
            if (isset($result[$key]))
            {
                if (is_array($result[$key]))
                {
                    $result[$key] = array($result[$key]);
                }
                $result[$key][] = $arg;
            }
            else
            {
                $result[$key] = $arg;
            }
        }
    }
}
```

此处有两点值得指出。如果在 `$_simple` 中的参数名称用完后仍遇到简单参数，则它会通过最后一个简单名称被添加到一个数组中。这正是 `paragraph()` 函数的工作方式。它只有一个简单参数名称 `'values'`，因此传入函数的简单参数列表最终会成为 `$values` 数组的元素：

`paragraph('One line','Another line',$variable,'Yet another line');`

变为

`'values' => array('One line', 'Another line', $variable, 'Yet another line');`

但是，如果没有传入名称，我们将无法存放任何非关联数组的参数。在这种情况下，我们使用 PHP 的 `user_error()` 函数来引发错误。它会打印出我们的错误消息并停止脚本，就像普通 PHP 错误一样。（你会在后续示例中多次看到 `user_error()` 函数。）

最后，为了清理工作，我们将对默认参数和简单参数列表的任何更改传回给调用函数。由于这两个数组是按引用传入的，对它们在此处所做的更改会更新原始变量。并且，由于它们被声明为静态的，这些更改在下次调用函数时仍然会存在。

```
$defaults = array_merge($defaults, $result['_defaults']);
$simple = $result['_simple'];
return $result;
}
```

对 `$_defaults` 的更改会合并到原始列表中，而 `$_simple` 的新值将替换旧值。

在 `image_src()` 函数中调用 `parse_arguments()` 后，如下所示，

`$p = parse_arguments($p, $_simple, $_defaults);`

我们得到一个数组 `$p`，其中包含原始调用中的所有属性值和其他参数。例如，从网页中的这一行 –

`image_src('/images/monkey.jpg');`

– 我们最终会在 `$p` 中得到以下值：

`$p = array('src'=>'/images/monkey.jpg', 'alt'=>'', 'border'=>0);`

具体到 `<IMG>` 标签，如果 `'alt'` 属性为空，我们将使用图像文件的名称（来自 `'src'` 属性）作为默认值：

```
if (empty($p['alt']))
$p['alt'] = $p['src'];
```

下一步是将对图像文件的引用转换为 HTML 标签。因此，我们将数组传递给 `get_attlist()` 函数。该函数从关联数组中获取键/值对，并将其重新格式化为一个 HTML 样式属性字符串。上一个示例将返回如下内容：

`src="/images/monkey.jpg" alt="/images/monkey.jpg" border="0"`

因此，我们只需添加标签本身的名称以及开合尖括号，即可得到以下内容，`image_tag()` 将其作为结果返回：

```
<img src="/images/monkey.jpg" alt="/images/monkey.jpg"
border="0">
```

在 `/functions/basic.php` 中定义的特殊常量 `STANDALONE` 对于 `<option>` 标签中类似于 `'selected'` 的属性很有用。因此，

`array('value'=>'CA','selected'=>STANDALONE)`

变为

`value="CA" selected`

仅为了得到一个简单的 `img` 标签，使用此函数可能看起来工作量很大。确实如此。回报是灵活性，代价是复杂度的增加。在高性能环境中，你可能最终会舍弃这段代码的部分内容。例如，你可以规定所有函数调用都将采用以下形式：

`my_function(array('param1'=>'value1', 'param2'=>'value2', ...))`

这样你就可以省略对 `parse_arguments()` 的调用，只需将传入的数组与 `$_defaults` 合并即可。或者，你可以在生产/开发环境中使用此类函数来生成不那么聪明、因而更快速的文件，然后将这些文件推送到你的服务器上。

## /BOOK/FUNCTIONS/HTML/ 中的函数

这些函数使创建常见 HTML 标签变得更加容易。此文件中的大多数函数都非常相似。

### ANCHOR_TAG()

此函数创建一个锚标签。

```
function anchor_tag()
{
    static $defaults = array(
        'href'=>''
        , 'text' => ''
        , 'value' => ''
        , 'allowed' => array('Common','accesskey','charset','href'
        ,'hreflang','rel','rev','tabindex','type','name','target'
        );
    static $simple = array('href','value');
    $p = func_get_args();
    $p = parse_arguments($p, $_simple, $defaults);
    if (empty($p['text']))
    {
        $p['text'] = $p['href'];
    }
    if (empty($p['value']))
    {
        $p['value'] = $p['text'];
    }
    $attlist = get_attlist($p);
    $output = "<a $attlist>$p['value']</a>";
    return $output;
}
```

使用锚标签时，每次只能期望两样东西：一个 href 属性以及位于开合 `<a>` 标签之间的文本。但是，name 属性可能更具描述性，且在客户端脚本中更有用。但大多数情况下，对此函数的调用看起来会像这样：

`anchor_tag('myurl.com/index.html', 'this is a great link');`

### PARAGRAPH()

此函数将根据调用方式，要么输出成对的 `<p>` 标签及其中间的所有内容，要么仅输出开头的 `<p>` 标签。
