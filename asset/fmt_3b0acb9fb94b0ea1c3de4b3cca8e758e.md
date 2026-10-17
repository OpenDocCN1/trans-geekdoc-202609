
如果你希望网页采用 GB2312 编码，同时使用 UTF-8 作为脚本内部编码，并且希望脚本控制 HTTP 输入和输出转换过程，则方法 #2 很有用。以下是 `php.ini` 设置：

```
mbstring.language = Neutral
mbstring.internal_encoding = UTF-8
mbstring.http_input = pass
mbstring.http_output = pass
mbstring.encoding_translation = Off
```

如果你希望网页采用 UTF-8 编码，同时使用 UTF-16 作为脚本内部编码，并且信任 PHP 引擎进行 HTTP 输入和输出编码转换，则方法 #3 很有用。以下是 `php.ini` 设置：

```
mbstring.language = Neutral
mbstring.internal_encoding = UTF-8
mbstring.http_input = GB2312
mbstring.http_output = GB2312
mbstring.encoding_translation = On
```

由于方法 #2 比其他方法更具挑战性，我编写了以下脚本为你提供一些思路：

### MbStringHttp.php 示例分析

### PHP 脚本代码

```php
<?php
#### MbStringHttp.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   mb_internal_encoding("UTF-8");

#- 处理 HTTP 输入转换
   $myRequest['English'] = "";
   $myRequest['ChineseUtf8'] = "";
   $myRequest['ChineseGb2312'] = "";
   foreach ($_REQUEST as $k => $v) {
      $myRequest[$k] = mb_convert_encoding($v,"UTF-8", "GB2312");
   }
   $r_English = $myRequest['English'];
   $r_ChineseUtf8 = $myRequest['ChineseUtf8'];
   $r_ChineseGb2312 = $myRequest['ChineseGb2312'];

#- 处理 HTTP 输出转换
   mb_http_output("GB2312");
   ob_start("mb_output_handler");

#- 生成 HTML 文档
   print("<html>");
   print('<meta http-equiv="Content-Type"'
      .' content="text/html; charset=gb2312"/>');
   print("<body>\n");
   print("<form action=MbStringHttp.php method=get>");
   print("English ASCII: <input name=English"
      ." value='$r_English' size=16><br>\n");
   print("Chinese UTF-8: <input name=ChineseUtf8"
      ." value='$r_ChineseUtf8' size=16><br>\n");
   print("Chinese GB2312: <input name=ChineseGb2312"
      ." value='$r_ChineseGb2312' size=16><br>\n");
   print("<input type=submit name=submit value=Submit>\n");
   print("</form>\n");

#- 将输入字符串输出回 HTML 文档
   print("<hr>");
   print("<pre>");
   print("{$myRequest['English']}\n");
   print("{$myRequest['ChineseUtf8']}\n");
   print("{$myRequest['ChineseGb2312']}\n");
   print("</pre>");
   print("</body>");
   print("</html>");

#- 将输入字符串转储到文件
   $file = fopen("\\temp\\MbStringHttp.txt", 'ab');
   $str = "--- Query String ---\n";
   fwrite($file, $str, strlen($str));
   if (array_key_exists('QUERY_STRING',$_SERVER)) {
      $str = $_SERVER['QUERY_STRING'];
   } else {
      $str = NULL;
   }
   fwrite($file, $str, strlen($str));

   $str = "--- Raw reqeust input ---\n";
   fwrite($file, $str, strlen($str));
   foreach ($_REQUEST as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }

   $str = "--- Converted reqeust input ---\n";
   fwrite($file, $str, strlen($str));
   foreach ($myRequest as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }
   fclose($file);
?>
```

### 测试输入

我用 IE 测试了这个脚本，并输入了以下字符串：

```
English ASCII: Hello world!
Spanish UTF-8: ¡Hola mundo!
Korean UTF-8: 여보세요 세계 !
Chinese UTF-8: 你好世界!
Chinese GB2312: ????¡
```

### 返回页面源码分析

返回页面正确显示了输入字符串。但源代码非常有趣：

```html
<html><meta http-equiv="Content-Type" content="text/html;
   charset=gb2312"/><body>
<form action=MbStringHttp.php method=get>
English ASCII: <input name=English value='Hello world!' size=16><br>
Spanish UTF-8: <input name=Spanish value='&iexcl;Hola mundo!'
   size=16><br>
Korean UTF-8: <input name=Korean value='&#50668;&#48372;&#49464;
   &#50836; &#49464;&#44228; !' size=16><br>
Chinese UTF-8: <input name=ChineseUtf8 value='ÄãºÃÊÀ½ç!' size=16><br>
Chinese GB2312: <input name=ChineseGb2312 value='&Ecirc;&Agrave;
   &frac12;&ccedil;&Auml;&atilde;&ordm;&Atilde;&pound;&iexcl;'
   size=16><br>
<input type=submit name=submit value=Submit>
</form>
<hr><pre>Hello world!
&iexcl;Hola mundo!
&#50668;&#48372;&#49464;&#50836; &#49464;&#44228; !
ÄãºÃÊÀ½ç!
&Ecirc;&Agrave;&frac12;&ccedil;&Auml;&atilde;&ordm;&Atilde;
   &pound;&iexcl;
</pre></body></html>
```

### 观察结果

*   当网页设置 `charset=gb2312` 时，某些 Unicode 字符会记录为 HTML 命名实体，如 `&iexcl;` 和 `&Ecirc;`。某些 Unicode 字符会记录为 HTML 数字实体，如 `&#50668;` 和 `&#48372;`。

*   当 UTF-8 编码的中文字符被复制到表单中时，它们会被记录为 GB2312 编码。

*   当 GB2312 编码的中文字符被复制到表单中时，它们会被记录为 HTML 命名实体。原因未知。

### 转储文件内容

我查看了转储文件 `\\temp\\MbStringHttp.txt`：

```
--- Query String ---
English=Hello+world%21&
Spanish=%26iexcl%3BHola+mundo%21&
Korean=%26%2350668%3B%26%2348372%3B%26%2349464%3B%26%2350836%3B+
   %26%2349464%3B%26%2344228%3B+%21&
ChineseUtf8=%C4%E3%BA%C3%CA%C0%BD%E7%21&
ChineseGb2312=%26Ecirc%3B%26Agrave%3B%26frac12%3B%26ccedil%3B
   %26Auml%3B%26atilde%3B%26ordm%3B%26Atilde%3B%26pound%3B%26iexcl%3B&
submit=Submit
--- Raw reqeust input ---
English = (Hello world!)
Spanish = (&iexcl;Hola mundo!)
Korean = (&#50668;&#48372;&#49464;&#50836; &#49464;&#44228; !)
ChineseUtf8 = (ÄãºÃÊÀ½ç!)
ChineseGb2312 = (&Ecirc;&Agrave;&frac12;&ccedil;&Auml;&atilde;&ordm;
   &Atilde;&pound;&iexcl;)
submit = (Submit)
--- Converted reqeust input ---
English = (Hello world!)
Spanish = (&iexcl;Hola mundo!)
Korean = (&#50668;&#48372;&#49464;&#50836; &#49464;&#44228; !)
ChineseUtf8 = (ä½ å¥½ä¸–ç•Œ!)
ChineseGb2312 = (&Ecirc;&Agrave;&frac12;&ccedil;&Auml;&atilde;&ordm;
   &Atilde;&pound;&iexcl;)
submit = (Submit)
```

### 结论

如果输入字符串被 Web 浏览器记录为 GB2312，我的脚本正确处理了 HTTP 输入和输出编码。对于记录为 HTML 实体的其他字符，你需要通过告诉用户正确输入数据来避免它们。

---

### 使用 MySQL 服务器管理非 ASCII 字符串

本章提供了关于使用 MySQL 服务器处理非 ASCII 字符的教程示例和说明。主题包括使用各种字符集编码在 MySQL 数据库中存储非 ASCII 字符；在向数据库插入数据和从数据库检索数据时管理编码转换；使用 UTF-8 编码的示例。

#### 相关章节

> 存储非 ASCII 字符到数据库
>
> 与数据库传输非 ASCII 字符
>
> MySqlUnicode.php - MySQL Unicode UTF-8 编码示例

#### 核心要点

*   MySQL 对非 ASCII 字符提供良好的支持。它提供多种编码（字符集）。

*   MySQL 允许我们在数据库、表或列级别指定编码。

*   MySQL 允许我们控制接收 SQL 语句和返回查询结果时的编码转换。

*   我的建议是对所有文本信息使用 UTF-8，关闭 MySQL 在接收 SQL 语句和返回查询结果时的编码转换，让 PHP 脚本处理 UTF-8 字符串。

---

## 存储非 ASCII 字符到数据库

本节介绍如何使用在列、表或数据库级别设置的不同字符集设置，在 MySQL 数据库中存储非 ASCII 字符。

MySQL 可以用多种编码在数据库中存储非 ASCII 字符，MySQL 称它们为字符集：

### 字符集与 MySQL 非 ASCII 字符传输

#### 字符集列表

| Charset | Description |
|---------|-------------|
| big5 | Big5 繁体中文 |
| dec8 | DEC 西欧 |
| cp850 | DOS 西欧 |
| hp8 | HP 西欧 |
| koi8r | KOI8-R Relcom 俄语 |
| latin1 | ISO 8859-1 西欧 |
| latin2 | ISO 8859-2 中欧 |
| swe7 | 7bit 瑞典语 |
| ascii | US ASCII |
| ujis | EUC-JP 日语 |
| sjis | Shift-JIS 日语 |
| cp1251 | Windows 斯拉夫语 |
| hebrew | ISO 8859-8 希伯来语 |
| tis620 | TIS620 泰语 |
| euckr | EUC-KR 韩语 |
| koi8u | KOI8-U 乌克兰语 |
| gb2312 | GB2312 简体中文 |
| greek | ISO 8859-7 希腊语 |
| cp1250 | Windows 中欧 |
| gbk | GBK 简体中文 |
| latin5 | ISO 8859-9 土耳其语 |
| armscii8 | ARMSCII-8 亚美尼亚语 |
| utf8 | UTF-8 Unicode |
| ucs2 | UCS-2 Unicode |
| cp866 | DOS 俄语 |
| keybcs2 | DOS Kamenicky 捷克-斯洛伐克语 |
| macce | Mac 中欧 |
| macroman | Mac 西欧 |
| cp852 | DOS 中欧 |
| latin7 | ISO 8859-13 波罗的海语言 |
| cp1256 | Windows 阿拉伯语 |
| cp1257 | Windows 波罗的海语言 |
| binary | 二进制伪字符集 |
| geostd8 | GEOSTD8 格鲁吉亚语 |

#### 指定字符集层级

要在数据库列中存储非 ASCII 字符，需要使用特定字符集定义该列。可在 3 个层级指定字符集：数据库、表和列。例如：

```
CREATE DATABASE db_name CHARACTER SET utf8
CREATE TABLE tbl_name (...) CHARACTER SET utf8
CREATE TABLE tbl_name (col_name CHAR(80) CHARACTER SET utf8, ...)
```

*   若在**数据库层级**指定字符集，则应用于该数据库中所有表的所有 `CHAR`、`VARCHAR` 和 `TEXT` 列。

*   若在**表层级**指定字符集，则应用于该表中所有 `CHAR`、`VARCHAR` 和 `TEXT` 列。

*   若在**列层级**指定字符集，则仅应用于该列。

*   建表语句中指定的列长度按字符级别计算，而非编码字节级别。

*   若在 `CHAR(n)` 列上使用 `utf8`，该列将需要 `3*n` 字节的存储空间。

#### 传输非 ASCII 字符

本节介绍将非 ASCII 字符从 PHP 脚本传输到 MySQL 数据库服务器，以及从 MySQL 服务器传回 PHP 脚本的基本设置和规则。

在 MySQL 中处理非 ASCII 字符，不仅要求使用正确的编码（字符集）设置表列，还要求为向数据库传输字符和从数据库传输字符设置正确的编码。

MySQL 提供以下全局变量控制客户端（PHP 脚本）与服务端（MySQL 数据库）之间传输字符所用的编码：

*   `character_set_server` - 服务器上所有数据库使用的字符集。
*   `character_set_database` - 服务器上默认数据库使用的字符集。
*   `character_set_client` - 客户端用于所有 SQL 语句的字符集。
*   `character_set_connection` - 服务器执行前将所有 SQL 语句转换为的字符集。
*   `character_set_results` - 服务器发回客户端前将所有返回结果转换为的字符集。

大多数情况下，应使客户端（PHP 脚本）使用与服务端（MySQL 服务器）相同的编码（字符集），这样传输字符时无需转换。

有时可能需要使用不同编码。例如，PHP 脚本使用 UTF-8，而 MySQL 表使用 GB2312。

可使用两个特殊的 `SET` 命令更改这些变量：

1.  `SET NAMES 'x'` 等同于以下三条语句：

    ```
    SET character_set_client = x;
    SET character_set_results = x;
    SET character_set_connection = x;
    ```
