
回答：
PHP 有 strpos() 函数，可在另一字符串中搜索子字符串。

### 81：如何修改字符串中字母的大小写？

回答：
可以使用 strtoupper、strtolower、ucfirst、ucwords 等函数来修改 PHP 字符串中字母的大小写。

### 82：如何在 PHP 中写入标准输出？

回答：
除了使用 print、printf、echo 函数外，还可以使用 fopen('PHP://stderr', 'w') 在 PHP 中写入标准输出。

### 83：如何读取文件的权限和所有权数据？

回答：
PHP 函数 stat() 返回一个关于文件的信息数组。

### 84：如何获取文件的完整物理路径？

回答：
可以使用 PHP 函数 dirname() 获取文件的完整物理路径。

### 85：如何在 PHP 中复制和移动文件？

回答：
PHP 分别使用 copy() 和 rename() 函数来复制和移动文件。在 Unix 上，rename() 函数无法跨文件系统移动文件。

### 86：如何从字符串中删除所有 HTML 和 PHP 标签？

回答：
可以使用 strip_tags() 函数从字符串中删除所有 HTML 和 PHP 标签。

### 87：如何在数组中查找元素？

回答：
PHP 函数 array_search() 用于在数组中搜索元素。这将返回找到的值的索引。

### 88：如何打开文件以进行写入？

回答：
可以使用 fopen() 函数写入文件。例如：$f = fopen("sample.txt", "w")；

### 89：ob_start() 在 PHP 中用于哪里？

回答：
此函数用于 PHP 中的输出缓冲。

### 90：如何在 PHP 中合并两个数组？

回答：
可以在 PHP 中使用 array_merge() 函数合并不同的数组。

### 91：为什么在 PHP 变量名前使用 @ 运算符？

回答：
@ 运算符在尝试访问未定义变量时会抑制任何警告/错误。

### 92：使用 var 关键字声明 PHP 变量是否有效？

回答：
已弃用，但使用 var 关键字声明 PHP 变量仍然有效。

### 93：fclose() 函数返回任何内容吗？

回答：
它不是 void 函数。它返回一个布尔值，指示文件关闭是否成功。

## 面向对象编程

### 94：PHP 支持多重继承吗？

回答：PHP 不支持多重继承。PHP 中的类只能扩展单个基类。

### 95：PHP 是纯面向对象语言吗？

回答：不是，PHP 不是纯面向对象语言。

### 96：PHP 支持方法/函数重载吗？

回答：PHP 不是强类型语言，因此在 PHP 中支持传统的函数重载意义不大。

### 97：PHP 支持 C++ 风格的运算符重载吗？

回答：不，PHP 不支持 C++ 风格的运算符重载。

### 98：PHP 支持类似 Java 的接口吗？一个类可以实现两个接口吗？

回答：是的，PHP 支持接口实现概念。一个类只能实现一个接口。

### 99：实现该接口的类可以覆盖接口常量吗？

回答：不，PHP 中的类不能覆盖接口常量。

### 100：如何强制销毁对象？

回答：当脚本终止时，对象会自动销毁。要强制销毁，可以使用 unset()。

### 101：如何在 PHP 中克隆现有对象？

回答：
可以在 PHP 中使用简单的赋值运算符来克隆现有对象。

### 102：如何在 PHP 中调用父类构造函数？

回答：
可以在 PHP 中使用 parent::constructor($value) 来完成此操作。

### 103：PHP 支持数据封装吗？

回答：
PHP 通过为类成员提供 public、private、protected 等访问说明符来支持数据封装。

### 104：PHP 支持异常处理吗？

回答：
是的，PHP 使用常规的 try/catch 块支持异常处理。

### 105：如果在没有可见性说明符的情况下声明类属性，它是 public、private 还是 protected？

回答：
类属性默认为 public。

## 正则表达式

### 106：什么是贪婪正则表达式匹配？PHP 正则表达式是贪婪的吗？如何解决这个问题？

回答：
正则表达式也称为 regex。正则表达式中的标准量词是贪婪的，意味着它们会尽可能多地匹配，只在必要时回溯以匹配正则表达式的其余部分。我们在正则表达式内使用“?”来抑制这种行为。

### 107：preg_replace 和 ereg_replace 有什么区别？

回答：
ereg_replace 使用基本版本的正则表达式，而 preg_replace 使用 Perl 兼容的正则表达式。

### 108：你能写一个 PHP 正则表达式来检查电子邮件地址是否有效吗？

回答：
```
/^[^@\s]+@([-a-z0-9]+\.)+[a-z]{2,}$/i
```

### 109：你能写一个 PHP 函数从 HTML 文档中提取 URL 吗？

回答：
```
function pc_link_extractor($s) {
    $a = array();
    if (preg_match_all('/<a\s+.*?href=[\"\' ]?([^\"\' >]*)[\"\' ]?[^>]*>(.*)<\/a>/i', $s, $matches, PREG_SET_ORDER)) {
        foreach($matches as $match) {
            array_push($a,array($match[1],$match[2]));
        }
    }
    return $a;
}
```

### 110：如何使用 PHP 的正则表达式从字符串 'http://xyz@a...' 中提取字符串 'abc.com'？

回答：
可以将 "/.*(@(.*))$/" 作为正则表达式模式与 preg_match() 函数一起使用。例如：

```
preg_match("/.*(@(.*))$/","http://xyz@abc.com",$data);
echo $data[1];
```

### 111：你能写一个 PHP 正则表达式来匹配字母数字字符吗？

回答：
```
[\w]
```

## Web 自动化

### 112：如何使用 PHP 获取网页内容？

回答：
可以使用 PHP Curl 扩展或 file_get_contents（一个库模块）来完成此操作。对于发送 POST 请求等高级选项，需要使用 Curl。

### 113：Curl 代表什么？PHP Curl 支持哪些协议？

回答：
Curl 代表 Client URL。PHP Curl 支持 http、https、ftp、gopher、telnet、dict、file 和 ldap 协议。

### 114：如何使用 PHP 克服 HTTP 的无状态特性？

回答：
需要使用 PHP 会话来克服 HTTP 的无状态特性。

### 115：如何使用 PHP 发送 SOAP 请求？

回答：
可以使用 PEAR 的 SOAP 类在 PHP 中发送 SOAP 请求。

### 116：如何使用 PHP 读取 RSS 提要？

回答：
可以使用 PEAR XML_RSS 类从不同网站读取 RSS 提要。

### 117：PHP 可用于网页抓取吗？

回答：
是的，PHP 可用于网页抓取，因为 PHP 可以动态检索网页内容，并使用各种选项对其进行解析。

## 高级 PHP

### 118：PHP 支持多线程吗？

回答：
PHP 没有内置的多线程支持。可以在 PHP 中模拟 fork。Forking 是多任务处理的一种方法，并且存在名为 Process Control Extension 的扩展来处理此问题。还有命令行 PHP 命令允许进程在 PHP 之外运行并将输出返回给 PHP。

### 119：可以使用 PHP 查询域名吗？

回答：
PHP 有一个名为 gethostbyname() 的函数，可用于查询域名。

### 120：gethostbyaddr() 返回的主机名总是正确的吗？

回答：
这不一定总是正确。恶意用户可以配置 DNS 服务器以返回不正确的主机名。可以使用 gethostbyname() 和 gethostbyaddr() 的组合来验证结果的正确性。

### 121：可以使用 PHP ping 主机吗？

回答：
可以使用 PEAR 的 Net_Ping 包 ping 主机以查看其是否可达。

```
$ping = new Net_Ping;
if ($ping->checkhost('www.vibrantpublishers.com')) {
  print 'Reachable';
} else {
  print 'Not reachable';
}
```

### 122：PHP 支持 FTP 吗？可以列出 PHP 提供的一些 FTP 函数吗？

