

## 第 II.8 章：使用来自网站的信息 299

使用 `file_get_contents()` 函数获取的页面 HTML 代码更为简单：

```html
<li><div class="yschttl href="http://www.php.net/"><p>PHP</p><a href=": Hypertext Preprocessor</a></div>
```

考虑到所有这些，为了让列表 II.8.3 正常工作，必须按照列表 II.8.5 所示进行修改。

### 列表 II.8.5. 从 Yahoo 搜索系统页面提取 URL

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://search.yahoo.com/search?p=PHP&sm=Yahoo%21+Search&fr=FP-tab-web-t&toggle=1&cop&ie=UTF-8";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "|<li>[\s]*<div>[\s]*<a[class=yschttl[^"]]+href=\"([^"]+)\"|";
// 对正则表达式进行搜索
preg_match_all($pattern, $contents);
```

使用列表 II.8.6 所示的脚本可以形成超链接列表。

### 列表 II.8.6. 从 Yahoo 搜索系统页面提取超链接

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://search.yahoo.com/search?p=PHP&sm=Yahoo%21+Search&fr=FP-tab-web-t&toggle=1&cop&ie=UTF-8";
// 加载页面内容。
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "<li>([\s]*<div>[\s]*a[\s]*class=yschtl[^"]]*href=\"([^"]+)\">([\s]*.*?)<a></li>";
// 对正则表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "<a href=\"$out[1][$i]\">$out[2][$i]</a><br>";
}
?>
```

### II.8.3. 从 Google 提取链接

与 Yahoo 不同，Google 没有惊喜——至少在本书编写时是如此。可以使用列表 II.8.7 所示的脚本生成 URL 列表。

### 列表 II.8.7. 使用 get_contents() 函数

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.google.com/search?hl=mysql&btnG=Google+Search";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正表达式
$pattern = "<a([\s]+class=1\s*)href=\"([^"]+)\"|";
// 对正表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "$out[1][$i].<br>";
}
?>
```

## 第 II.8 章：使用来自网站的信息 301

使用列表 II.8.8 所示的脚本可以形成超链接列表。

### 列表 II.8.8. 从 Google 搜索页面提取超链接

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.google.com/search?hl=en&q=MySQL&btnG=Google+Search";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "|<a[\s]+class=[^"]]*href=\"([^"]+)\"";
```

### II.8.4. 从 MSN 提取链接

与 Yahoo 类似，MSN 搜索系统使用客户端发送的 HTTP 头。因此，应该使用 PHP 加载的文件。可以使用列表 II.8.9 所示的脚本形成 URL 列表。

### 列表 II.8.9. 从 MSN 搜索页面提取 URL

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://search.msn.com/results.aspx?q=Apache&FORM=MSNH&srch_type=0";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
```

可以使用列表 II.8.10 所示的脚本形成超链接列表。

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://search.msn.com/results.aspx?q=Apache&FORM=MSNH&srch_type=0";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "|<li>[\s]*<div>[\s]*<a[class=yschttl[^"]]+href=\"([^"]+)\">([\s]*.*?)<a></li>";
// 对正则表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "<a href=\"$out[1][$i]\">$out[2][$i]</a><br>";
}
?>
```

### II.8.5. 从 AltaVista 提取链接

与 Yahoo 不同，Google 没有惊喜——至少在本书编写时是如此。可以使用列表 II.8.11 所示的脚本生成 URL 列表。

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.google.com/search?hl=mysql&btnG=Google+Search";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "<a([\s]+class=1\s*)href=\"([^"]+)\"|";
// 对正表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "$out[1][$i].<br>";
}
?>
```

### 第 II.8 章：使用来自网站的信息

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.google..com/search?=
=mysql";
// 加
页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "<a([\s]+class=1\s*)href=\"([^"]+)\"|";
// 对正表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "$out[1][$i].<br>";
}
?>
```

### 第 II.8 章：使用来自网站的信息

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.google.com/search?hl=mysql";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "<a([\s]+class=1\s*)href=\"([^"]+)\"|";
// 对正表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "$out[1][$i].<br>";
}
?>
```

### II.8.11. 从 提取链接

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.altavista.com/search?=php";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "<li>([\s]*<div>[\s]*a[\s]*class=yschtl[^"]]*href=\"([^"]+)\">([\s]*.*?)<a></li>";
// 对正则表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "<a href=\"$out[1][$i]\">$out[2][$i]</a><br>";
}
?>
```

### II.8.12. 从  提取超链接

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.altavista.com/search?q=php";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "<li>([\s]*<div>[\s]*a[\s]*class=yschtl[^"]]*href=\"([^"]+)\">([\s]*.*?)<a></li>";
// 对正则表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "<a href=\"$out[1][$i]\">$out[2][$i]</a><br>";
}
?>
```

### II.8.6. 从 XML 文件提取汇率

在从欧洲银行网站加载的 XML 文件中，感兴趣的标签有：

- <Cube time='2006-01-20'> - 当前日期
- <Cube currency='USD' rate='1.2068'/> - 欧元兑美元的汇率（1.00 值为 1.2068）

创建一个通用脚本，提取列表 II.8.13 所示的所有货币汇率。

### 列表 II.8.13. 提取汇

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "http://www.ecb.eu/stats/euroref/euroref-daily.xml";
// 加载页面内容
$contents = file_get_contents($url);

// 提取日期
$pattern = "|Cube time=([^']+*)'|";
// 对正则表达式进行搜索
preg_match($pattern, $contents, $out);
echo "日期为 $out[1].<br><br";

// 提取货币汇率
$pattern = "|Cube currency=([^']+*)' rate='([^']+*)'|";
// 对正则表达式进行搜索
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// 显示搜索结果
for($i=0; $i < count($out[1]); $i++) {
    echo "1. $out[1][$i]. - " . $out[2][$i]." EUR<br";
}
?>
```

图 II.8.1. 列表 II.8.13 脚本的执行结果

