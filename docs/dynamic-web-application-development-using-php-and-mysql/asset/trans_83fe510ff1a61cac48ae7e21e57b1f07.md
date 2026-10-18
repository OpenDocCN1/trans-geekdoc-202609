
用于指定网页中所显示信息的结构和样式。浏览器使用这些标签来组织它们之间的文本，并将指定的标记应用于开始和结束标签之间的任何内容。例如，由`<P>`标签定义的段落元素用于将文本组织成段落。

```
<P>some text in paragraph one . . .</P>
<P>some text in paragraph two . . .</P>
```

最新的HTML规范4.01建议元素名称使用大写字母（属性名称使用小写字母），尽管实际上HTML不区分大小写，所以这只是一个约定而非要求：

> 元素名称用大写字母书写。……属性名称用小写字母书写。……请记住，在HTML中，元素和属性名称不区分大小写；这一约定旨在提高可读性。（Raggett 等人，1999年）

我们将在第4章看到，XML和XHTML的元素名称使用小写字母。因此，当你在本书中看到标记时，就会立刻明白：如果元素名称是大写，那么示例是HTML 4.01；如果是小写，那么该标记是XML或XHTML。

段落和其他类似元素可以被视为结构元素，因为它们以某种语义方式组织内容。换句话说，它们帮助我们理解内容的含义。段落通常将一些涉及同一主题的句子组合在一起。同样，诸如`<H1>`这样的主标题元素标签也可以被视为结构性的。将文本组织成标题、副标题、段落等，是在不同文本块彼此关联的方式上提供结构。然而，它并不指定这些标题、副标题等的外观。相比之下，HTML还包含许多与文档表现样式相关的标签，用于改变字体、颜色或其他样式方面。这类标签的一个简单例子是粗体（`<B>`）标签：

```
<B>this text will be presented in bold face</B>
```

这样的标签专门用于定义文档的一部分在显示时的外观，与文本的结构或语义无关。我们不会在本章中介绍表现性标记。处理页面表现的首选方式是使用层叠样式表（CSS），我们将在第4章中介绍。

## 创建HTML文档

最简单的HTML文档包含一组少量的结构和内容元素。这些是HTML、HEAD、TITLE和BODY。HTML文档中的第一个和最后一个内容应始终是包围根（HTML）元素的标签，即`<HTML> . . . </HTML>`。在HTML元素内部，有一个嵌套的HEAD元素，`<HEAD> . . . </HEAD>`，其中包含文档头部信息，包括文档标题。TITLE元素嵌套在HEAD元素内部，使用`<TITLE>`和`</TITLE>`标签。TITLE元素的内容出现在浏览器标题栏的顶部、历史记录列表中，以及如果你为页面创建书签，还会出现在书签文件中。BODY元素位于HEAD元素之后。BODY元素表示浏览器窗口中显示的页面内容。以下是一个具有这组最小元素的HTML文档：

```
<HTML>
    <HEAD>
        <TITLE> The title of the web page </TITLE>
    </HEAD>
    <BODY> body content of the web page </BODY>
</HTML>
```

## 内容类型

在文档主体中，内容通常被组织成文本信息块，如标题、段落、列表和表格。主体中也可能有其他媒体类型，如图像、声音片段和影片。媒体类型是某种多用途互联网邮件扩展（MIME）类型，它定义了可以在互联网上使用的特定文件类型。自HTML 4以来，首选的术语是内容类型，因为媒体类型更恰当地应用于输出设备的类型。无论如何，HTML文档的类型是'text/html'，但这类文档可能包含对不同类型内容的引用。HTML提供了大量标签来组织文档内容的结构，包括可能包含在其中的所有其他内容类型。在本章中，我们将介绍主要的组织元素：标题、段落、列表、表格和表单。

## 文本元素

网页内容的很大一部分基于文本的管理。文本的结构可以使用标题、副标题和段落来组织。某些其他类型的内容可以有效地按列表（可以以某种方式排序）或表格来结构化。文本的某些语义方面也可以包含在标记中，例如提供强调或指示引文。在本节中，我们将介绍一些有助于组织HTML页面内容的基本结构元素。

组织基于文本的内容的一种非常常见的方式是使用标题、副标题和段落。H1、H2、H3、H4、H5和H6元素可用于不同级别的标题和副标题。H1是最大的标题，H6是最小的。由于标题通常比后面的文本大，使用超过前两三级标题可能不太合理。在许多浏览器中，最小的标题类型比标准段落文本还要小。

正如我们已经看到的，段落元素的HTML语法是`<P>`。你还应在每个段落末尾添加结束标签`</P>`，以使元素“格式良好”，不过大多数浏览器即使没有结束标签也能正确显示页面。这是最小化（minimisation）的一个方面，是SGML的一个特性，意味着并非所有元素都需要结束标签，如果元素的结束可以从文档结构的其他部分推断出来，例如另一个段落的开始推断前一段的结束。浏览器通常会在段落元素之前留一个空行。在下面的示例中，我们使用一个H1元素作为主标题，H2元素作为副标题，正文段落用`<P> ... </P>`标签包围。

这个示例还包含了HTML中的注释语法，如下所示：

```
<!-- this is a comment -->
```

我们将在全书中使用这种注释语法来指示每个示例所引用的源文件。

```
<HTML>
<HEAD>
<TITLE>Versions of HTML</TITLE>
</HEAD>
<BODY>
<!-- File: example3-1.htm -->
<H1>Versions of HTML</H1>
<H2>HTML 1.0</H2>
<P>
The first version of HTML dates from 1991, and was developed by Tim Berners-Lee. It was very different from the HTML we know today...
</P>
<H2>HTML 2.0</H2>
<P>
The second version of HTML, in 1996, was an attempt to standardise the language, which was being widely implemented by different vendors' web browsers...
</P>
</BODY>
</HTML>
```

图3.1显示了该页面在Internet Explorer 7中的外观。请注意标题、副标题和段落的文本大小不同。

图3.1 标题、副标题和段落

![](img/b2471264f405d17994ef173e4b9cec92_79_0.png)

## 3.4 HTML文档类型

浏览器通常能够处理HTML元素的省略，并且实际上对格式不良的HTML语法相当宽容。然而，良好的实践不仅是要编写格式良好的HTML，还要为文档指定类型定义。这有助于浏览器通过将文档结构与特定定义匹配来渲染文档，该定义规定了HTML元素和属性应如何组织。

自HTML 2.0以来，公共文档类型定义（DTD）已可用于指定HTML文档的类型。HTML 4.01中有三个这样的DTD：‘strict’（严格）、‘transitional’（过渡）和‘frameset’（框架集）（Raggett 等人，1999年）。与‘strict’版本相比，‘transitional’和‘frameset’版本允许更广泛的元素和更灵活的结构，并允许表现与内容和结构的广泛混合。我们将在后面的章节中更详细地介绍DTD以及如何使用它们来验证文档的结构，但与此同时，我们声明我们的HTML标记使用‘strict’类型定义。为此，我们需要在HTML文档顶部添加以下行：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
```

这表示文档应遵循HTML 4.01结构的严格规则。‘DOCTYPE’指的是一个公开可用的、用于指定HTML文档类型的DTD。以下是我们第一个示例，添加了必要的定义：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
    <HEAD>
        <TITLE>Versions of HTML</TITLE>
    </HEAD>
    <BODY>
        <H1>Versions of HTML</H1>
        <H2>HTML 1.0</H2>
        <P>
The first version of HTML dates from 1991, and was developed by Tim Berners-Lee.
It was very different from the HTML we know today. . .
        </P>
        <H2>HTML 2.0</H2>
        <P>
The second version of HTML, in 1996, was an attempt to standardise the language,
which was being widely implemented by different vendors' web browsers. . .
        </P>
    </BODY>
</HTML>
```

## 3.5 组织文本

除了将页面组织成标题和段落之外，我们还可以将许多其他结构元素应用于HTML文档。在本节中，我们将介绍一些有助于组织文本的元素。
