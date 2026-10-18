

# 嵌套模板实战

本质上，可以将嵌套模板视为构建模块，每个模块都能无缝嵌套于另一个之中，形成一个连贯且结构化的整体。对于 GitforGits 书店而言，嵌套模板的实用性在考虑构成网站的各个不同部分时显而易见——例如页眉、页脚、侧边栏、主内容等。这些部分中的每一个都可以是一个独立的模板，而在构建完整页面时，这些模板可以嵌套在主模板中。这种模块化方法确保了更新的便捷性、页面间的一致性以及统一的设计语言。

## 构建框架

我们将首先为书店创建一个基础模板。这个基础模板可以包含嵌套模板的占位符，以确保内容渲染的灵活性。

```
{{define "base"}}
<html>
<head>
    <title>GitforGits Bookstore</title>
</head>
<body>
    {{template "header" .}}
    {{template "content" .}}
    {{template "footer" .}}
</body>
</html>
{{end}}
```

在上面的代码片段中，`"header"`、`"content"` 和 `"footer"` 是可以插入嵌套模板的命名占位符。

## 创建页眉

页眉通常在整个网站中保持一致，可以将其单独制作成一个模板。它可能包含书店的标志、导航链接，或许还有一个搜索栏。

```
{{define "header"}}
<div class="header">
    <img src="logo.png" alt="GitforGits Logo">
    <ul class="navigation">
        <li>Home</li>
        <li>Bestsellers</li>
        <li>Genres</li>
    </ul>
</div>
{{end}}
```

## 制作内容

`"content"` 占位符正是嵌套模板灵活性真正闪耀的地方。根据页面不同——无论是畅销书列表、作者传记还是书评——内容模板都可以动态替换。

```
{{define "booklist"}}
<div class="book-list">
    {{range .Books}}
    <div class="book">
        <h2>{{.Title}}</h2>
        <p>By {{.Author}}</p>
    </div>
    {{end}}
</div>
{{end}}
```

## 封装页脚

页脚与页眉类似，保持相对一致，包含联系方式、服务条款和社交媒体链接等信息。

```
{{define "footer"}}
<div class="footer">
    <p>Contact us at contact@gitforgits.com</p>
    <ul class="social-media">
        <li>Facebook</li>
        <li>Twitter</li>
    </ul>
</div>
{{end}}
```

要构建完整网页，这些嵌套模板可以在基础模板中渲染。使用 Go 的模板执行函数，可以将特定的内容模板（如 `"booklist"`）注入到基础模板中，从而形成一个完整且结构化的网页。

# 设计主页面布局

任何网站的主页面都类似于橱窗。对于 GitforGits 书店来说，它是虚拟入口，邀请用户探索其中丰富的文学宝藏。它不仅应展示多样性，还应让用户一窥特色功能，例如畅销书、新书上架和用户评论。这就是设计与功能相结合的地方，确保引人入胜且流畅的浏览体验。

## 构建基础布局

要开始，请尝试可视化构成主页面结构的组件。想象一个网站布局，包含一个带有导航链接的显著页眉、一个显示书籍的动态内容区域，以及一个包含网站基本信息的页脚。这些组件中的每一个都可以作为单独的模板来制作，从而实现产品的模块化设计和可重用性。

```
{{define "base"}}
<html>
<head>
    <title>GitforGits Bookstore: Home</title>
</head>
<body>
    {{template "header" .}}
    {{template "mainContent" .}}
    {{template "footer" .}}
</body>
</html>
{{end}}
```

## 设计页眉

页眉既要视觉吸引人，又要功能高效。它需要容纳品牌标志、主要导航链接，以及可能用于用户查找特定书名的搜索栏。

```
{{define "header"}}
<div class="header">
    <img src="logo.png" alt="GitforGits Logo">
    <ul class="navigation">
        <li>Home</li>
        <li>Bestsellers</li>
        <li>New Arrivals</li>
        <li>Genres</li>
    </ul>
    <div class="search">
        <input type="text" placeholder="Search for books...">
        <button>Search</button>
    </div>
</div>
{{end}}
```

## 构建动态内容区域

主页面的主要部分就是奇迹发生的地方。书籍可以分为不同的部分，例如“精选”、“畅销书”或“用户推荐”。对于每个类别，可以使用循环遍历书籍列表，动态显示它们。

```
{{define "mainContent"}}
<div class="content">
    <section class="featured">
        <h2>Featured Books</h2>
        {{range .FeaturedBooks}}
        <div class="book">
            <img src="{{.ImageURL}}" alt="{{.Title}}">
            <h3>{{.Title}}</h3>
            <p>By {{.Author}}</p>
        </div>
        {{end}}
    </section>
    <section class="bestsellers">
        <h2>Bestsellers</h2>
        {{range .BestsellingBooks}}
        <div class="book">
            <img src="{{.ImageURL}}" alt="{{.Title}}">
            <h3>{{.Title}}</h3>
            <p>By {{.Author}}</p>
        </div>
        {{end}}
    </section>
    <section class="recommendations">
        <h2>User Recommendations</h2>
        {{range .UserRecommended}}
        <div class="book">
            <img src="{{.ImageURL}}" alt="{{.Title}}">
            <h3>{{.Title}}</h3>
            <p>By {{.Author}}</p>
        </div>
        {{end}}
    </section>
</div>
{{end}}
```

## 勾勒完整页脚

页脚通过提供基本链接、联系信息和社交媒体连接来完成主页面。它确保用户无论身处页面何处，都能访问必要的资源。

```
{{define "footer"}}
<div class="footer">
    <ul>
        <li>About Us</li>
        <li>Contact</li>
        <li>Terms of Service</li>
    </ul>
    <div class="social-icons">
        <img src="facebook-icon.png">
        <img src="twitter-icon.png">
    </div>
    <p>&copy; 2023 GitforGits Bookstore</p>
</div>
{{end}}
```

这种模块化方法确保每个部分都能得到应有的关注。从页眉的欢迎拥抱，到主内容中多样的文学展示，再到资源丰富的页脚，每个像素都经过精心打磨。

