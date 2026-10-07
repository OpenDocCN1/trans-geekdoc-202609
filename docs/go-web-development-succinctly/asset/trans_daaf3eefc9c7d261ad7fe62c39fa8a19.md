

## 在模板中使用条件判断

你可以使用 `{{if}}` `{{else}}` `{{end}}` 将条件表达式的评估交给模板处理。

Go 支持几个处理基本类型的函数，例如 `eq`（等于）、`ne`（不等于）或 `gt`（大于），你可以使用它们来构建表达式。

在模板中使用条件表达式的用法可以通过一个示例来演示。

假设我们只对人口小于 5,000,000 的群体感兴趣。其他所有数据都将被视为巨大且不显示具体数字。

代码列表 16 显示了我们的模板。

> 代码列表 16：带有条件表达式的模板

```html
<html
<head>
<title>City Search</title>
</head>
<body>
<h1>Search Results</h1>
<table border='1'>
<tr>
<th>City</th>
<th>Country Code</th>
<th>Population</th>
</tr>
{{range}}
<tr>
<td>{{.Name}}</td>
<td>{{.CountryCode}}</td>
<td>
{{if gt .Population 5000000}} <b>HUGE</b>
{{else}} {{.Population}}
{{end}}
</td>
</td>
</tr>
{{end}}
</table>
</body>
</html>
```

图 18 显示了结果。

# 搜索结果

| 市 | 国家代码 | 人口 |
|---|---|--|
| Stoke-on-Trent | GBR | 252000 |
| Tokyo | JPN | HUGE |
| Tokorozawa | JPN | 325809 |
| Tokushima | JPN | 269649 |
| Tokuyama | JPN | 107078 |
| Tokai | JPN | 99738 |
| Yamatokoriyama | JPN | 95165 |
| Bialystok | POL | 283937 |
| Tokat | TUR | 99500 |
| Vladivostok | RUS | 606200 |

图 17：在模板中使用条件判断显示人口数值

## 第 5 章 创建一个 RESTful JSON API

我们已经学习了许多内容，所以让我们看看能否利用这些知识做一些实用的事情。

在第 1 章中，我们研究了为什么 Go 是创建 Web 服务的极佳选择，例如：它通过轻量级线程模型进行大规模扩展的能力、模块化编码的简易性，以及与常用工具（如加密库、安全协议，当然还有 HTTP 服务器）集成的能力。

在本章中，我将演示如何创建一个 RESTful Web 服务，它可以接收 JSON 请求并返回 JSON 响应，以便对数据库进行 CRUD（创建、读查、更新和删除）操作。

（实际上，我在这里稍微耍了个小懒。为了最小化应用程序的复杂性，我将创建一个 CRUD 应用。更新功能将留给读者作为练习）

这个应用程序将使用我们目前为止学到的关于服务、路由和访问数据库的知识。在构建过程中，我将向你展示如何设计和开发一个典型的 Web 服务。它不会是完美的或生产就的，但它应该能让你直观感受到在 Go 中构建这类服务有多简单。

# RESTful APIs

如果你是一个开发者，或者曾经和开发者共处过，你一定听过 REST。鉴于它近年来吸引的巨大关注，你可能会认为它也是一个新概念。但事实并非如此。事实上，它和 Web 本身一样老。

REST 仅仅是为了处理多年来开发的数百种不同协议，这些协议旨在让计算机使用相同的语言在网络之间进行通信。

这些协议中包括 SOAP（因为它依赖 XML 作为传输机制，需要大量的数据和计算能力，随着移动设备的普及，它开始淡出主流）、JMS（特定于 Java 应用程序，因此并不真正适用于广泛采用）以及 XML-RPC（像 SOAP 一样，使用 XML 但没有实现 SOAP 拥有的标准）。

与所有这些方法一样，REST 背后的目标是让计算机轻松地共享数据，同时保持足够的透明度，让人类观察者理解他们正在做什么。

REST 提供的是保持轻量级同时实现此能力。它的方法对于使用 Web 本身采用的成熟方法的开发者来说是他们熟悉的。

# 为什么呢？

嗯，考虑一个你在浏览器中访问的网站。你输入该网站的 URL，网站背后的程序可以分析 URL 以理解你的意图。在静态网站中，你只是输入指向 Web 服务器上文件资源的 URL；但在采用 Web 服务的网站中，你可以有效地将 API 作为命令行入口，不仅针对资源，还针对程序 API 暴露的特定操作。

考虑开放电影数据库网站 (http://www.omdbapi.com)，它提供了一个免费的 REST API 来访问电影信息。你只需要构造 URL，指定你想要它提供的内容。

如果你从 https://www.omdbapi.com/ 开始，你将得到图 19 中的首页。

![](img/cdabbe899d95a91197e7ec37cc1c8048_48_0.png)

# 使用方法

如果你从 https://www.omdbapi.com/ 开始，你将得到图 19 中的首页。

图 18：访问电影数据库 API
如果你使用 (t) 参数，你会得到一些有趣的内容：https://www.omdbapi.com/?t=starwars

> "Title:Star Wars Episode IV - A Hope","Year:1977","Rating:PG","Released:25 May 1977","Runtime:121 min","Genre:Action,Adventure,Fantasy","Director:George Lucas","Actors:Mark Hamill, Carrie Fisher, Oscar Fisher, James Earl, Harrison Ford, Alec Guinness, Peter Cushing","Plot:Luke Skywalker joins forces with a Jedi Knight, a cheeky pilot, and droids to save the galaxy from the Empire's world-destroying battle-station, while attempting to rescue Princess Leia from Darth Vader.","Awards:None","Oscars:Won 6 wins & 28 nominations","Poster:https://images-na.amazon.com/images/M/MV5BMjQ3OTcwMTQt40Zi00000Ym00Y2YYYYY0OTQ@@._XkFtYMTQ0MDA0NDI1_V1_X300.jpg","Metscore:92","imdbRating:8.7","imdbVotes:958,001","imdbDB:tt006759","Type:Movie","Response:True

# 使用

JSON（JavaScript Object Notation）。对于 XML 来说，这已经非常简洁了。许多 XML 是深度嵌套的，解析起来是场噩梦，因此偏好 JSON。

除了轻量级和易于客户端解析之外，JSON 也具有人类可读性。嗯，勉强吧。你可以通过浏览器的开发者控制台或安装扩展程序来整理响应。

图 21 显示了安装了 JSON Formatter-add 后 Firefox 上的输出。

```json
{
  "Title": "Star Wars: Episode IV - A Hope",
  "Year": "1977",
  "Rating": "PG",
  "Released": "25 May 1977",
  "Runtime": "121 min",
  "Genre": "Action,Adventure,Fantasy",
  "Director": "George Lucas",
  "Actors": "Mark Hamill, Carrie Fisher, Oscar Fisher, James Earl, Harrison Ford, Alec Guinness, Peter Cushing",
  "Plot": "Luke Skywalker joins forces with a Jedi Knight, a cheeky pilot, and droids to save the galaxy from the Empire's world-destroying battle-station, while attempting to rescue Princess Leia from Darth Vader.",
  "Awards": "None",
  "Oscars": "Won 6 wins & 28 nominations",
  "Poster": "https://images-na.amazon.com/images/M/MV5BMjQ3OTcwMTQt40Zi00000Ym00Y2YYYYY0OTQ@@._XkFtYMTQ0MDA0NDI1_V1_X300.jpg",
  "Metscore": "92",
  "imdbRating": "8.7",
  "imdbVotes": "958,001",
  "imdbDB": "tt006759",
  "Type": "Movie",
  "Response": "True"
}
```

图 20：格式化后的 JSON

# RESTful Web 服务

我们将在本章中构建类似的服务。我们的应用程序将允许用户输入以下任何路径，并获得所描述的结果：

