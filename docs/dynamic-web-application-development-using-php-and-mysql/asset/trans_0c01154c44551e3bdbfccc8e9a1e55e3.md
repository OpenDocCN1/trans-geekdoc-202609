
**图 3.3** 嵌套有序列表和无序列表在浏览器中的显示效果

![](img/b2471264f405d17994ef173e4b9cec92_86_0.png)

## 定义列表

定义列表与其他类型的列表略有不同，因为它们是按术语表的形式组织的。定义列表的外部元素使用 `<DL> . . . </DL>`（定义列表）标签。在该元素内部，出现一组或多组术语和定义。在每一组中，术语由 `DT`（定义术语）元素定义，定义则出现在 `DD`（定义列表定义）元素中。下面是一个包含定义列表的 HTML 文档示例：

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
    <HEAD>
        <TITLE>Markup Languages</TITLE>
    </HEAD>
    <!-- File: example3-4.htm -->
<BODY>
    <DL>
        <DT> SGML </DT>
        <DD> Standard Generalised Markup Language </DD>
        <DT> HTML </DT>
        <DD> HyperText Markup Language </DD>
        <DT> XML </DT>
        <DD> eXtensible Markup Language </DD>
    </DL>
</BODY>
</HTML>
```

图 3.4 展示了该定义列表在 Mozilla Firefox 2 中的显示效果。在这个浏览器中，定义和术语在字号或样式上没有区别，只有布局受到影响。不过，我们可以添加 `EM` 或 `STRONG` 标签，以进一步在语义上区分定义与术语。

**图 3.4** 定义列表

![](img/b2471264f405d17994ef173e4b9cec92_87_0.png)

## 3.7 HTML 中的属性

到目前为止，我们已经看到了许多 HTML 元素，但这些元素都没有包含属性。然而，许多 HTML 标签都可以带有属性。其中许多属性可以被归类为表现性属性；事实上，在 HTML 中使用属性进行表现，很好地说明了元素与属性在用法上的差异。元素用于定义文档的内容，而属性往往为这些元素提供额外的配置。如果我们将元素的表现视为其元数据的一部分，那么就可以理解，属性是一种将元数据应用于 HTML 元素的好方式。然而，属性并不仅限于定义表现。它们也可以用于某些结构方面，我们将在接下来的示例中看到。

### 图像

刚才我们说过，目前讨论的是内容和结构而非表现，因此此时引入图像乍看起来可能有点奇怪。然而，网页中的图像是一种内容类型的实例，这意味着它是页面内容的一部分，而不是页面的表现。只不过这种内容恰好具有视觉特征。可以使用 `IMG` 空元素将图像添加到网页中，但与之前看到的空元素（`BR` 和 `HR`）不同，`IMG` 元素没有属性则无法使用。关键属性是 `src`，它指定要包含在页面中的图像文件的 URI。网络上最常见的图像文件类型是 GIF（Graphics Interchange Format，图形交换格式）、JPEG（Joint Photographic Experts Group，联合图像专家组）和 PNG（Portable Network Graphics，便携式网络图形），因为它们的文件体积相对较小，因此下载速度也相当快。GIF 和 PNG 文件通常用于绘图，而 JPEG 用于照片，因为 JPEG 能比 GIF 处理更多颜色，并且比 PNG 拥有更灵活的压缩算法。PNG 格式是在 Unisys 持有 GIF 压缩算法专利时开发的，但它在渲染超过 256 种颜色方面也优于 GIF 文件，尽管相应文件往往比 GIF 更大。

除了定义图像的来源外，我们还必须使用 `alt` 属性提供一个替代文本值。这既有助于在图像无法加载时提供文本替代（例如，用户为了速度而在浏览器中禁用了图像加载），也有助于为无法看到图像的用户提供可读出的文本。下面是一个以 GIF 文件为来源的 `IMG` 元素：

```html
<IMG src="logo.gif" alt="WebHomeCover Logo">
```

可应用于图像的其他属性是 `height` 和 `width`，它们可用于在页面上按原始尺寸缩放图像，但更常用于指定图像的实际尺寸（以像素为单位），使浏览器能够更快地加载页面，因为浏览器可以在下载文件之前预先估算所需的显示空间：

```html
<IMG src="logo.gif" alt="WebHomeCover Logo" height="115" width="102">
```

### 链接

万维网最重要的方面之一就是链接（又称超链接或网络链接），它使我们能够从一个网络资源跳转到另一个资源，无论该资源在网络上的何处。链接有两个端点，称为锚点：源锚点位于当前文档中，目标锚点是被链接的网络资源（文档、图像、声音文件等）。单击网页中的链接即可获取所链接的网络资源。HTML 中链接的完整细节相当复杂，因此这里只介绍基础知识。

HTML 文档中用于锚点的元素名是 `A`，最重要的属性是 `href`（超文本引用），它包含所链接资源的 URI。例如，下面是一个指向 WebHomeCover 网站 URI 的锚点：

```html
Click <A href="http://www.webhomecover.com">here</A> for a great
insurance deal...
```

锚点元素主体中的文本（`here`）是显示在浏览器中的实际超链接。

并非所有锚点元素中的 URI 都需要包含完整的网址。许多用于 Web 应用的锚点会链接到同一应用中的其他页面，因此 URI 可以是使用本地路径的文件名。例如，下面的锚点引用本地目录中的一个文件：

```html
<A href="aboutus.htm">About Us</A>
```

也可以使用相对路径。这里，我们假设当前文件夹（用 `.` 表示）下有一个 `images` 文件夹，其中存储着一个图像文件：

```html
<A href="./images/map.gif">Find Us</A>
```

除了链接到其他文件，HTML 页面中的锚点还可以链接到文档的特定部分。如果目标锚点不是完整的 URI，而是在文档内部，那么可以在链接的目标端使用锚点元素。例如，我们可能希望链接到文档中包含我们保险政策某些条款与条件的那一部分。若要链接到同一文档的某一部分，源锚点中使用的 URI 是目标锚点的名称，前面加一个井号，例如：

```html
<A href="#terms">terms and conditions</A>
```

在这个示例中，我们假设同一文档中有一个名为 `terms` 的目标锚点。它将在文档的其他地方使用锚点元素的 `id` 属性来定义，例如：

```html
<A id="terms">Terms and Conditions</A>
```

单击源锚点的超链接会将用户带到包含目标锚点的文档部分。下面的标记展示了源锚点和目标锚点如何在同一个文档中出现：

```html
Our insurance is offered according to our standard <A href="#terms">terms and
conditions</A> which you should read carefully before making a claim...

blah blah blah...

<H2><A id="terms">Terms and Conditions</A></H2>
WebHomeCover reserve the right to...
```

当目标锚点在另一个文档的某个部分时，也可以使用同样的方法。唯一的不同是锚点名称前面要加上所在页面的 URI，例如：

```html
<A href="legal.htm#terms">terms and conditions</A>
```

在这种情况下，我们假设 `terms` 锚点位于另一个名为 `legal.html` 的文档中。也可以使用完整地址：

```html
<A href="http://www.webhomecover.com/legal.htm#terms">
    terms and conditions
</A>
```

与文本一样，图像也可以通过将 `IMG` 元素嵌套在锚点元素中而用作链接锚点，例如：

```html
<A href="home.html">
    <IMG src="logo.gif" alt="WebHomeCover Logo">
</A>
```

这是实现我们在第 2 章中看到的“左上角站点徽标”模式的有用技巧，即单击公司徽标总是会带你前往主页。

### 电子邮件链接

锚点也可以用于电子邮件链接。为此，只需在 `href` 属性中使用 `mailto` 值，其格式如下：

```html
<A href="mailto:help@webhomecover.com">Email the help desk</A>
```

当单击“给帮助台发送电子邮件”时，Web 浏览器可能会打开你的电子邮件客户端来撰写邮件，不过，这确实取决于浏览器配置，因此其行为无法保证。

