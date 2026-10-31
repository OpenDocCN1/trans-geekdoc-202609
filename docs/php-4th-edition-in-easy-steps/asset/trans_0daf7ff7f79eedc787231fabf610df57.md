
# OpenWeatherMap XML 响应处理

OpenWeatherMap 的响应可以作为 XML 文件交付，可使用 PHP `asXml()` 函数指定文件名将其写入 Web 服务器的 `/htdocs` 文件夹中。这可以在 Web 浏览器中检查，以发现检索到的数据的性质、XML 元素名称、属性名称和结构：

![image](images/1p.jpg)
通过为四个变量分配字符串值开始一个 PHP 脚本，这些变量将用于设置响应参数

```
<?php
$city \= ‘New York’ ;
$units \= ‘imperial’ ;
$mode \= ‘xml’ ;
$id \= ‘28df3c64f387cf55026e0de3fb8beaa4’ ;
```

![image](images/commonp.jpg)

param.php

![image](images/2p.jpg)
接下来，添加一条语句，使用指定的参数值构建请求字符串

```
$request \=
‘http://api.openweathermap.org/data/2.5/forecast?’.
‘q=’.$city.’&units=’.$units.’&mode=’.$mode.’&APPID=’.$id ;
```

![image](images/3p.jpg)
现在，添加一条语句，使用请求字符串参数加载 XML 数据，或退出

```
$xml \= simplexml_load_file( $request )
or die( ‘Unable to load data!’ ) ;
```

![image](images/4p.jpg)
当收到响应时，尝试将内容作为 XML 文件写入 Web 服务器的 `/htdocs` 目录

```
try
{
$xml->asXml( ‘params.xml’ ) ;
// Statement to be inserted here (Step 5).
}
catch( Exception $e )
{
echo ‘Error : ‘.$e->getMessage() ;
}
```

![image](images/pg174_2.jpg)

params.xml

![image](images/5p.jpg)
插入一条语句，将浏览器重定向以查看新创建的 XML 文档

```
header( ‘Location: params.xml’ ) ;
```

![image](images/6p.jpg)
将 PHP 脚本保存在 Web 服务器的 `/htdocs` 目录中，命名为 `params.php`，然后通过 HTTP 打开页面以检查检索到的响应的 XML 内容

![image](images/pg183_1.jpg)

![image](images/forget.jpg)

响应将仅包含当前条件的天气数据。

![image](images/pg183_2.jpg)

这里突出显示的数据是最感兴趣的。它可以使用每个包含的元素名称和属性名称检索。

## 选择组件

![image](images/pg184_1.jpg)

在检查了从 OpenWeatherMap 检索到的响应数据 [此处第 183 页](#chapter11.xhtml#load) 后，选定的组件可以动态地合并到 PHP 粘性表单 XML 应用中：

![image](images/1p.jpg)
开始一个 PHP 脚本，通过加载页面头文件来提供横幅图像

```
<?php
include( ‘includes/weather-header.html’ ) ;
```

![image](images/2p.jpg)
接下来，添加一个条件测试，查看页面是否通过表单提交打开

```
if( $_SERVER[ ‘REQUEST_METHOD’ ] == ‘POST’ )
{
// Statements to be inserted here (Steps 3-6).
}
```

![image](images/commonp.jpg)

weather.php

![image](images/3p.jpg)
在条件测试块内部，为四个变量分配参数字符串值

```
$city \= ( empty( $_POST[ ‘city’ ] ) ) ? ”New York”
: $_POST[ ‘city’ ] ;
$units \= ‘imperial’ ;
$mode \= ‘xml’ ;
$id \= ‘28df3c64f387cf55026e0de3fb8beaa4’ ;
```

![image](images/4p.jpg)
接下来，在条件测试块内部，插入一条语句，使用指定的参数值构建请求字符串

```
$request \=
‘http://api.openweathermap.org/data/2.5/weather?’.
‘q=’.$city.’&units=’.$units.’&mode=’.$mode.’&APPID=’.$id ;
```

![image](images/5p.jpg)
现在，在条件测试块内部，插入一条语句，使用参数加载 XML 数据，或退出

```
$xml \= simplexml_load_file( $request )
or die( ‘Unable to load data!’ ) ;
```

![image](images/6p.jpg)
最后，插入语句以输出检索到的数据

```
$icon \= ‘http://openweathermap.org/img/w/’.
$xml->weather[ ‘icon’ ].’.png’ ;
echo ‘<h1>Today in ‘.$xml->city[ ‘name’ ] ;
echo ‘ it\’s ‘.$xml->weather[ ‘value’ ].
’<img src=’.$icon.’></h1>’ ;
echo ‘<ul><li>Temperature : ‘.$xml->temperature[‘value’] ;
echo ‘&deg; ‘.$xml->temperature[ ‘unit’ ] ;
echo ‘<li>Wind : ‘.$xml->wind->speed[ ‘name’ ] ;
echo ‘<li>Humidity : ‘.$xml->humidity[‘value’].’&#37;</ul>’ ;
```

![image](images/hot.jpg)

请注意，如果表单在没有用户输入的情况下提交，则会分配默认城市值。

![image](images/hot.jpg)

`icon` 属性的值是 PNG 图像文件的名称。当与路径和 `.png` 文件扩展名连接时，它提供适当的天气图像。

![image](images/7p.jpg)
在测试块之后，添加语句以创建表单

```
echo ‘<form method=”POST” action=”weather.php”>’ ;
echo ‘<fieldset><legend>Enter City Name</legend>’ ;
echo ‘<input type=”text” name=”city”>’ ;
echo ‘<input type=”submit”
name=”submission” value = ”Get Weather”>’ ;
echo ‘</fieldset></form>’ ;
```

![image](images/8p.jpg)
最后，在脚本中，加载页面页脚文件以显示表示该应用所采用的技术图标

```
include( ‘includes/weather-footer.html’ ) ;
```

![image](images/pg181_1.jpg)

weather-header.html

weather-footer.html

![image](images/9p.jpg)
将 PHP 脚本保存在 Web 服务器的 `/htdocs` 目录中，命名为 `weather.php`，然后通过 HTTP 打开页面并提交表单以查看默认纽约位置的天气。输入另一个城市名称并重新提交以查看该城市的天气报告

![image](images/pg185_1.jpg)

![image](images/pg181_3.jpg)

iesweather.png

tech.png

![image](images/pg185_2.jpg)

![image](images/forget.jpg)

`action` 属性指定此脚本文件以使表单保持粘性。

## 摘要

• XML 元素必须各自具有开始和结束标签，并且正确嵌套才能形成良好的格式。
• PHP 具有一个名为 `SimpleXML` 的 XML 解析器，可以将 XML 文档作为分层树结构加载到内存中。
• `simplexml_load_file()` 函数创建 `SimpleXMLElement` 对象的结构。
• `SimpleXML` 对象的结构描述了外部和内部 XML 元素之间的父子关系。
• `SimpleXML` 数据结构的每个成员都是一个节点。
• 顶级节点是 `SimpleXML` 对象本身的直接子后代。
• 可以使用 `->` 对象运算符引用节点，以寻址分层树结构的每一代。
• `children()` 方法返回所有子节点，可用于循环遍历树节点以检索每个节点的内容。
• 可以通过在节点名称后在括号之间用引号引起来说明属性名称来引用属性。
• RSS 订阅以 XML 格式提供定期更新的数据。
• XML 订阅通常是包含顶级 `<channel>` 元素的 XML 文档，该元素包含 `<item>` 元素。
• Web 服务可能提供静态 URL 或 API，允许您在 URL 请求中指定参数。
• 参数值由 `=` 字符指定，并在 `?` 之后附加到 URL，并由 `&` 分隔。
• `SimpleXML` 对象可以使用 `asXml()` 函数作为服务器上的 XML 文件写入。
• `SimpleXML` 对象的选定组件可以动态地合并到 PHP 应用中。

[![image](images/ibc1.jpg)](https://iescourses.com/)

[![image](images/ibc.jpg)](http://www.ineasysteps.com)

[![image](images/bcover.jpg)](http://www.ineasysteps.com)

